<script setup>
const webGroups = [
  {
    id: 'jd',
    name: 'JD.com',
    cases: [
      {
        id: 'jd-account',
        query: `Create a new account with username 'alex_jones', password 'MySecurePass123!', and phone number '13987654321'.`,
        video: '/VRBench_Web/outputs/JD/macro_000_00_HOME__ACCOUNT_CREATED_SUCCESS_item_original/recording.mp4',
      },
      {
        id: 'jd-review',
        query: `Filter to show only fresh items in the supermarket section, pick the seventh one, leave a 5-star review saying 'These avocados were perfectly ripe and creamy, excellent for guacamole', and submit it.`,
        video: '/VRBench_Web/outputs/JD/macro_000_00_HOME__REVIEW_SUBMITTED_SUCCESS_item_s7/recording.mp4',
      },
      {
        id: 'jd-checkout',
        query: 'Buy 3 pieces of the second item priced above $5 from the supermarket section, choose the first option, ship to my usual address with cash on delivery.',
        video: '/VRBench_Web/outputs/JD/macro_001_00_HOME__CHECKOUT_BUY_NOW_SUCCESS_item_s5/recording.mp4',
      },
    ],
  },
  {
    id: 'github',
    name: 'GitHub',
    cases: [
      {
        id: 'gh-branch',
        query: 'Navigate to repositories and filter for private ones, then open the first private repository and create a new branch called feature-auth from the main source.',
        video: '/VRBench_Web/outputs/github/macro_000_00_HOME__NEW_BRANCH_SUCCESS_item_repo_9/recording.mp4',
      },
      {
        id: 'gh-pr',
        query: `Find my private repositories, open the first one, create a pull request from the feature branch to main with title 'Add user authentication module', and submit it.`,
        video: '/VRBench_Web/outputs/github/macro_001_00_HOME__PR_CREATE_SUCCESS_item_repo_9/recording.mp4',
      },
      {
        id: 'gh-issue',
        query: `Create a new issue in the first private repository, title it 'Authentication bug in login flow', and submit it.`,
        video: '/VRBench_Web/outputs/github/macro_001_00_HOME__ISSUE_CREATE_SUCCESS_item_repo_9/recording.mp4',
      },
      {
        id: 'gh-profile',
        query: 'Update my profile name to Alex Johnson and save the changes.',
        video: '/VRBench_Web/outputs/github/macro_002_00_HOME__PROFILE_UPDATE_SUCCESS_item_original/recording.mp4',
      },
    ],
  },
  {
    id: 'medium',
    name: 'Medium',
    cases: [
      {
        id: 'medium-schedule',
        query: `Start writing a new story, set the title to 'The Midnight Garden', write the body content 'Under the pale moonlight, the old garden whispered secrets only the night could hear. Roses bloomed with silver petals, and the fountain sang a melody of forgotten dreams.', enable publishing, open publish options, continue to confirmation, schedule it for November 18, 2021 at 9:18 AM, and confirm the schedule.`,
        video: '/VRBench_Web/outputs/medium/macro_000_00_HOME__SCHEDULE_POST_SUCCESS_item_original/recording.mp4',
      },
      {
        id: 'medium-subscription',
        query: 'Upgrade to the monthly membership plan using card payment with number 4532123456789012, name Alex Johnson, and CVV 789, then complete the purchase.',
        video: '/VRBench_Web/outputs/medium/macro_000_00_HOME__SUBSCRIPTION_SUCCESS_item_original/recording.mp4',
      },
      {
        id: 'medium-profile',
        query: 'Update my profile name to John Doe.',
        video: '/VRBench_Web/outputs/medium/macro_001_00_HOME__PROFILE_UPDATE_SUCCESS_item_original/recording.mp4',
      },
      {
        id: 'medium-publish',
        query: `Write and publish a story titled 'The Future of Artificial Intelligence' with the body: 'Artificial intelligence is rapidly transforming our world. From self-driving cars to advanced healthcare diagnostics, AI is becoming an integral part of our daily lives. As we look to the future, the potential of AI seems limitless, but it also raises important ethical questions. How can we ensure that AI is developed and used responsibly? This article explores the current state of AI and its future implications.'`,
        video: '/VRBench_Web/outputs/medium/macro_001_00_HOME__PUBLISH_POST_SUCCESS_item_original/recording.mp4',
      },
    ],
  },
  {
    id: 'skyscanner',
    name: 'Skyscanner',
    cases: [
      {
        id: 'skyscanner-booking',
        query: 'Find American Airlines flights from LHR to JFK, traveling on September 16, 2029 in economy class. Book the American Airlines flight that comes up in the search results, choose standard baggage and standard seat, then complete the booking with first name Alex, last name Johnson, email alex.j@email.com, and card number 4111111111111111. Accept the terms and confirm the booking.',
        video: '/VRBench_Web/outputs/skyscanner/macro_001_00_HOME__BOOKING_COMPLETE_DIRECT_item_flight_3/recording.mp4',
      },
      {
        id: 'skyscanner-alert',
        query: `Find flights from London Heathrow to New York JFK for January 22, 2029 in economy class, then search for Aer Lingus flights in the results, open the matching one, and create a price alert named 'Aer Lingus JFK Alert' with email 'traveler@example.com'.`,
        video: '/VRBench_Web/outputs/skyscanner/macro_088_00_HOME__PRICE_ALERT_CREATED_item_flight_9/recording.mp4',
      },
    ],
  },
  {
    id: 'twitter',
    name: 'Twitter',
    cases: [
      {
        id: 'twitter-tweet',
        query: `Compose and post a tweet that says 'Excited to share that I just completed my 100th day of coding! #100DaysOfCode #coding'.`,
        video: '/VRBench_Web/outputs/twitter/macro_000_00_HOME__TWEET_POST_SUCCESS_item_original/recording.mp4',
      },
      {
        id: 'twitter-profile',
        query: `Update my profile bio to 'Experienced software engineer specializing in full-stack web development and cloud architecture' and change my display name to 'Alex Chen', then save the changes.`,
        video: '/VRBench_Web/outputs/twitter/macro_001_00_HOME__PROFILE_UPDATE_SUCCESS_item_original/recording.mp4',
      },
    ],
  },
  {
    id: 'youtube',
    name: 'YouTube',
    cases: [
      {
        id: 'youtube-like',
        query: 'From trending videos filtered to show ones longer than 3 minutes, watch the fourth video and like it.',
        video: '/VRBench_Web/outputs/youtube/macro_001_00_HOME__WATCH_LIKE_SUCCESS_item_v4/recording.mp4',
      },
      {
        id: 'youtube-comment',
        query: `Go to trending videos, allow location access, filter for videos longer than 2000 seconds, open the first one, then post this comment and submit it: 'This music is so calming, perfect for studying. Thanks for uploading!'`,
        video: '/VRBench_Web/outputs/youtube/macro_001_00_HOME__WATCH_COMMENT_SUCCESS_item_v3/recording.mp4',
      },
    ],
  },
]
</script>

<template>
  <div class="case-demonstration">
    <h1 class="section-title">Automatic Verified GUI Trajectory Collection Based on FSM</h1>

    <div class="task-rows">
      <div
        v-for="group in webGroups"
        :key="group.id"
        class="task-row"
      >
        <div class="task-header">
          <div class="task-label">{{ group.name }}</div>
          <div class="task-subtitle">Synthetic web tasks & verified trajectories</div>
        </div>

        <div class="video-grid">
          <div
            v-for="item in group.cases"
            :key="item.id"
            class="video-card"
          >
            <div class="case-query">
              <span class="query-label">Query</span>
              <p class="query-text">{{ item.query }}</p>
            </div>
            <div class="video-wrapper">
              <video
                :src="item.video"
                controls
                preload="metadata"
                class="video-player"
              >
                Your browser does not support the video tag.
              </video>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
.case-demonstration {
  padding: 80px 40px;
  max-width: 1400px;
  margin: 0 auto;
  background: #ffffff;
}

.section-title {
  font-size: 32px;
  font-weight: 700;
  color: #000000;
  text-align: center;
  margin-bottom: 50px;
  letter-spacing: -0.5px;
}

.task-rows {
  display: flex;
  flex-direction: column;
  gap: 32px;
}

.task-row {
  background: linear-gradient(to bottom, #fafafa 0%, #fafafa 85px, #ffffff 85px);
  border-radius: 16px;
  padding: 0;
  box-shadow: 0 2px 12px rgba(0, 0, 0, 0.06);
  border: 1px solid #e8e8ed;
  overflow: hidden;
  transition: all 0.3s ease;
}

.task-row:hover {
  box-shadow: 0 4px 20px rgba(0, 0, 0, 0.1);
  transform: translateY(-2px);
}

.task-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 20px 24px;
  background: transparent;
  border-bottom: 1px solid #e8e8ed;
}

.task-label {
  font-size: 22px;
  font-weight: 700;
  color: #1d1d1f;
  text-align: left;
  letter-spacing: -0.3px;
}

.task-subtitle {
  font-size: 14px;
  color: #6e6e73;
}

.video-grid {
  display: flex;
  flex-direction: column;
  gap: 20px;
  padding: 24px;
  background: #ffffff;
}

.video-card {
  background: #ffffff;
  border-radius: 10px;
  overflow: hidden;
  box-shadow: 0 1px 4px rgba(0, 0, 0, 0.08);
  transition: all 0.25s ease;
  border: 1px solid #e8e8ed;
  display: flex;
  flex-direction: column;
  gap: 12px;
  padding: 16px;
}

.video-card:hover {
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.12);
  transform: translateY(-3px);
  border-color: #0071e3;
}

.case-query {
  padding: 12px 16px;
  text-align: center;
  border-radius: 10px;
  background: linear-gradient(135deg, #f2f2f5 0%, #ffffff 60%);
  box-shadow: 0 4px 10px rgba(0, 0, 0, 0.08);
}

.query-label {
  font-size: 12px;
  font-weight: 600;
  text-transform: uppercase;
  color: #888888;
}

.query-text {
  margin: 6px 0 0;
  font-size: 15px;
  color: #1d1d1f;
  line-height: 1.45;
  font-weight: 600;
}

.video-wrapper {
  width: 100%;
  position: relative;
  background: #f0f0f0;
  overflow: hidden;
  aspect-ratio: 16 / 9;
}

.video-player {
  position: absolute;
  inset: 0;
  width: 100%;
  height: 100%;
  object-fit: contain;
  background: #000;
}

.video-player::cue {
  font-family: 'Droid Serif', 'Times New Roman', serif;
}

@media (max-width: 1024px) {
  .case-demonstration {
    padding: 40px 20px;
  }
}
</style>
