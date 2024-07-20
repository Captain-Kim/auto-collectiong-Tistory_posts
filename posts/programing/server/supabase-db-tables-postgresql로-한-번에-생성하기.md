<pre id="code_1721490151003" class="typescript" data-ke-language="typescript" data-ke-type="codeblock"><code>-- tripbookmarks 테이블 생성 및 기본 키 설정
create table
  "tripbookmarks" (
    "bookmark_id" uuid not null unique,
    "bookmark_created_at" timestamp with time zone not null,
    "bookmark_trip_id" uuid not null,
    "bookmark_buddy_id" uuid not null
  );

alter table "tripbookmarks"
add primary key ("bookmark_id");

-- payments 테이블 생성 및 기본 키 설정
create table
  "payments" (
    "payment_id" uuid not null unique,
    "payment_buddy_id" uuid not null,
    "payment_totalAmount" numeric not null,
    "payment_currency" text not null,
    "payment_status" text not null,
    "payment_approved_at" timestamp with time zone not null
  );

alter table "payments"
add primary key ("payment_id");

-- storylikes 테이블 생성 및 기본 키 설정
create table
  "storylikes" (
    "storylikes_id" uuid not null unique,
    "storylikes_created_at" timestamp with time zone not null,
    "storylikes_story_id" uuid not null,
    "storylikes_buddy_id" uuid not null
  );

alter table "storylikes"
add primary key ("storylikes_id");

-- contract 테이블 생성 및 기본 키 설정
create table
  "contract" (
    "contract_id" uuid not null unique,
    "contract_created_at" timestamp with time zone not null,
    "contract_trip_id" uuid not null,
    "contract_buddy_id" uuid not null,
    "contract_start_date" timestamp with time zone not null,
    "contract_end_date" timestamp with time zone not null,
    "contract_isPending" boolean not null,
    "contract_isLeader" boolean not null,
    "contract_isValidate" boolean not null,
    "contract_validate_date" timestamp with time zone not null
  );

alter table "contract"
add primary key ("contract_id");

-- buddies 테이블 생성 및 기본 키 설정
create table
  "buddies" (
    "buddy_id" uuid not null unique,
    "buddy_created_at" timestamp with time zone not null,
    "buddy_nickname" text not null unique,
    "buddy_email" text not null unique,
    "buddy_temperature" float (53) not null,
    "buddy_isPro" boolean not null,
    "buddy_isOnBoarding" boolean not null,
    "buddy_following_counts" integer not null,
    "buddy_follower_counts" integer not null,
    "buddy_sex" text,
    "buddy_birth" timestamp with time zone,
    "buddy_preferred_theme1" text,
    "buddy_preferred_theme2" text,
    "buddy_preferred_theme3" text,
    "buddy_preferred_buddy1" text,
    "buddy_preferred_buddy2" text,
    "buddy_preferred_buddy3" text,
    "buddy_mbti" text,
    "buddy_region" text,
    "buddy_introduction" text,
    "buddy_login_id" text unique,
    "buddy_profile_pic" text
  );

alter table "buddies"
add primary key ("buddy_id");

-- stories 테이블 생성 및 기본 키 설정
create table
  "stories" (
    "story_id" uuid not null unique,
    "story_created_at" timestamp with time zone not null,
    "story_created_by" uuid not null,
    "story_media" text not null,
    "story_overlay" jsonb not null,
    "story_likes_counts" integer not null
  );

alter table "stories"
add primary key ("story_id");

-- follow 테이블 생성 및 기본 키 설정
create table
  "follow" (
    "follow_id" uuid not null unique,
    "follow_created_at" timestamp with time zone not null,
    "follow_following_id" uuid not null,
    "follow_follower_id" uuid not null
  );

alter table "follow"
add primary key ("follow_id");

-- trips 테이블 생성 및 기본 키 설정
create table
  "trips" (
    "trip_id" uuid not null unique,
    "trip_created_at" timestamp with time zone not null,
    "trip_title" text not null,
    "trip_content" text not null,
    "trip_master_id" uuid not null,
    "trip_max_buddies_counts" integer not null,
    "trip_start_date" timestamp with time zone not null,
    "trip_end_date" timestamp with time zone not null,
    "trip_final_destination" text not null,
    "trip_meet_location" text not null,
    "trip_theme1" text not null,
    "trip_theme2" text not null,
    "trip_theme3" text not null,
    "trip_wanted_buddies1" text not null,
    "trip_wanted_buddies2" text not null,
    "trip_wanted_buddies3" text not null,
    "trip_wanted_sex" text not null,
    "trip_start_age" integer not null,
    "trip_end_age" integer not null,
    "trip_thumbnail" text not null,
    "trip_isValidate" boolean not null
  );

alter table "trips"
add primary key ("trip_id");

-- follow 테이블의 follow_follower_id 컬럼을 buddies 테이블의 buddy_id 컬럼과 외래 키 설정
alter table "follow"
add constraint "follow_follow_follower_id_foreign" foreign key ("follow_follower_id") references "buddies" ("buddy_id");

-- follow 테이블의 follow_following_id 컬럼을 buddies 테이블의 buddy_id 컬럼과 외래 키 설정
alter table "follow"
add constraint "follow_follow_following_id_foreign" foreign key ("follow_following_id") references "buddies" ("buddy_id");

-- payments 테이블의 payment_buddy_id 컬럼을 buddies 테이블의 buddy_id 컬럼과 외래 키 설정
alter table "payments"
add constraint "payments_payment_buddy_id_foreign" foreign key ("payment_buddy_id") references "buddies" ("buddy_id");

-- trips 테이블의 trip_id 컬럼을 contract 테이블의 contract_id 컬럼과 외래 키 설정
alter table "trips"
add constraint "trips_trip_id_foreign" foreign key ("trip_id") references "contract" ("contract_id");

-- storylikes 테이블의 storylikes_story_id 컬럼을 stories 테이블의 story_id 컬럼과 외래 키 설정
alter table "storylikes"
add constraint "storylikes_storylikes_story_id_foreign" foreign key ("storylikes_story_id") references "stories" ("story_id");

-- storylikes 테이블의 storylikes_buddy_id 컬럼을 buddies 테이블의 buddy_id 컬럼과 외래 키 설정
alter table "storylikes"
add constraint "storylikes_storylikes_buddy_id_foreign" foreign key ("storylikes_buddy_id") references "buddies" ("buddy_id");

-- tripbookmarks 테이블의 bookmark_buddy_id 컬럼을 buddies 테이블의 buddy_id 컬럼과 외래 키 설정
alter table "tripbookmarks"
add constraint "tripbookmarks_bookmark_buddy_id_foreign" foreign key ("bookmark_buddy_id") references "buddies" ("buddy_id");

-- tripbookmarks 테이블의 bookmark_trip_id 컬럼을 trips 테이블의 trip_id 컬럼과 외래 키 설정
alter table "tripbookmarks"
add constraint "tripbookmarks_bookmark_trip_id_foreign" foreign key ("bookmark_trip_id") references "trips" ("trip_id");

-- stories 테이블의 story_created_by 컬럼을 buddies 테이블의 buddy_id 컬럼과 외래 키 설정
alter table "stories"
add constraint "stories_story_created_by_foreign" foreign key ("story_created_by") references "buddies" ("buddy_id");

-- contract 테이블의 contract_trip_id 컬럼을 trips 테이블의 trip_id 컬럼과 외래 키 설정
alter table "contract"
add constraint "contract_contract_trip_id_foreign" foreign key ("contract_trip_id") references "trips" ("trip_id");

-- contract 테이블의 contract_buddy_id 컬럼을 buddies 테이블의 buddy_id 컬럼과 외래 키 설정
alter table "contract"
add constraint "contract_contract_buddy_id_foreign" foreign key ("contract_buddy_id") references "buddies" ("buddy_id");</code></pre>
<ul style="list-style-type: disc;" data-ke-list-type="disc">
<li>실제 사용했던 코드라 코드는 길다.</li>
<li>잘 작동한다.</li>
<li>한계
<ul style="list-style-type: disc;" data-ke-list-type="disc">
<li>supabase postgreSQL로 위 코드를 생성하면 nullable 설정과 uique설정은 잘 되지만, 외래키 설정에 문제가 있는 것 같다. 문법에는 오류가 없으나 이는 테스트 해봐야 함.</li>
<li>cascade 설정 안 됨</li>
</ul>
</li>
</ul>