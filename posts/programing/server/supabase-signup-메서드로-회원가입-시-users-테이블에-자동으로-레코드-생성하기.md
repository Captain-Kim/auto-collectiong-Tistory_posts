<pre id="code_1721498759419" class="sql" data-ke-language="sql" data-ke-type="codeblock"><code>CREATE OR REPLACE FUNCTION public.handle_new_user_custom() 
RETURNS TRIGGER AS $$ 
DECLARE
    new_nickname TEXT;
BEGIN
    -- 기본 닉네임 생성
    new_nickname := 'user_' || substring(md5(random()::text), 1, 8);

    -- nickname이 이미 존재하는지 검사
    WHILE EXISTS (SELECT 1 FROM public.buddies WHERE buddy_nickname = new_nickname) LOOP
        -- 중복 발생 시 다른 유니크한 닉네임 생성
        new_nickname := 'user_' || substring(md5(random()::text), 1, 8);
    END LOOP;

    INSERT INTO public.buddies (buddy_id, buddy_email, buddy_nickname, buddy_profile_pic) 
    VALUES (
        NEW.id, 
        NEW.email, 
        new_nickname,
        CASE 
            WHEN NEW.raw_user_meta_data-&gt;&gt;'avatar_url' IS NOT NULL 
            THEN NEW.raw_user_meta_data-&gt;&gt;'avatar_url' 
            ELSE NULL 
        END
    ); 
    RETURN NEW; 
END; 
$$ LANGUAGE plpgsql SECURITY DEFINER;

-- 새로운 트리거 생성
CREATE TRIGGER on_auth_user_created_custom 
AFTER INSERT ON auth.users 
FOR EACH ROW 
EXECUTE FUNCTION public.handle_new_user_custom();</code></pre>
<p data-ke-size="size16">&nbsp;</p>
<p data-ke-size="size16">그냥 복붙하지 마시고 테이블 이름과 컬럼 이름을 잘 보고 사용하시기 바람. 본인 프로젝트에 실제로 쓰인 코드임.</p>