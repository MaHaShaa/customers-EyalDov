# Hey Eyal! Welcome to Your Social Media Automation System 🚀

Let me walk you through everything you need to know to get your automated video posting system up and running!

---

## What We've Built For You

Remember our goal? We wanted to make your life easier by creating a system that:

1. **Watches your Dropbox folder** for new videos
2. **Automatically validates** the video quality (checks resolution, format, etc.)
3. **Posts to 4 platforms** without you lifting a finger:
   - YouTube Shorts
   - Facebook Reels
   - Instagram Reels
   - TikTok (once they approve our app)
4. **Tracks everything** in Airtable so you always know what's uploaded where
5. **Alerts you** via Telegram if something goes wrong

**The magic:** You just drop a video in Dropbox, and within seconds it's on its way to all your social media accounts!

---

## What You'll Need

Before you start, make sure you have:

- ✅ **Accounts on all platforms**
  - Dropbox (any plan works)
  - YouTube channel
  - Facebook Business Page
  - Instagram Business or Creator account
  - TikTok account (we're waiting for approval)

- ✅ **Admin access** to all these accounts
  - You need to be the owner or have full permissions

- ✅ **Important: Use the same email for n8n and Dropbox**
  - Your n8n instance email should match your Dropbox account email
  - This prevents OAuth authentication issues

- ✅ **A computer** (not phone)
  - Mobile doesn't work well for developer console stuff

- ✅ **One video ready to test** (for validation)
  - Make sure it's 1080x1920 (vertical), 15-60 seconds long

---

## The Setup Order

We'll do this in a specific order because some platforms depend on others:

### 1️⃣ **Dropbox**
This is where you'll upload videos. We need to connect Dropbox to our automation so it can trigger everything.

### 2️⃣ **YouTube**
Next up is YouTube because it's straightforward and independent of the others.

### 3️⃣ **Facebook**
Facebook is the foundation for Instagram, so we do it third. This one takes a bit longer because we need to get special tokens.

### 4️⃣ **Instagram**
Instagram uses the same setup as Facebook (they're owned by the same company), so this is quick once Facebook is done.

### 5️⃣ **TikTok** (Pending Approval)
We submitted our application on November 3, 2025, and we're waiting for their approval. Usually takes 5-7 business days.

---

## What You'll Be Doing

For each platform, the setup follows the same pattern:

1. **Create a developer app** (filling out forms)
2. **Get credentials** (passwords and IDs)
3. **Give the app permission** to post on your behalf
4. **Test it** to verify everything works

---

## Important Things to Know

### About Tokens and Manual Renewal

Tokens are like temporary passwords that let our automation post on your behalf.

| Platform | Manual Action Required | Frequency |
|----------|------------------------|-----------|
| Dropbox | ⚠️ **Yes** | Every ~7 days |
| YouTube | ❌ No | Auto-renews |
| Facebook | ⚠️ **Yes** | Every 50 days |
| Instagram | ⚠️ **Yes** (same as Facebook) | Every 50 days |
| TikTok | ❌ No | Auto-renews daily |

**Token Renewal Process:**

**Dropbox (every ~7 days):**
- Reconnect OAuth credentials in n8n
- Takes 2 minutes

**Facebook/Instagram (every 50 days):**
- Generate new Page Access Token
- Update in n8n
- Takes 2 minutes

---

## Upload Limits (The YouTube Bottleneck)

Each platform has daily limits on how many videos you can upload:

- **YouTube:** 6 videos/day ⚠️ **(This is our bottleneck)**
- Facebook: ~50 videos/day
- Instagram: ~25 reels/day
- TikTok: ~10 videos/day

The system is configured to upload **6 videos per day maximum** because that's YouTube's limit.

---

## What Happens After Setup

Once you're done with all the setup:

1. **Drop a video** in your Dropbox `/first_upload` folder
2. **Within seconds**, our system:
   - Validates the video (checks if it's the right format)
   - Creates a tracking record in Airtable
   - Generates a public URL
   - Sends it to all platforms
3. **You get notifications:**
   - ✅ Telegram message if video is valid
   - ⚠️ Telegram alert if something's wrong
4. **Check Airtable** to see upload status for all platforms

That's it! No more manual uploading to 4 different apps.

---

## Video Requirements (Super Important!)

For the automation to work, your videos must meet these specs:

✅ **Format:** MP4
✅ **Orientation:** Vertical (portrait mode - like you're holding your phone upright)
✅ **Resolution:** 1080 x 1920 pixels
✅ **Aspect Ratio:** 9:16 (vertical)
✅ **Duration:** 15-60 seconds (recommended)
✅ **File Size:** Under 50 MB (keep it small)
✅ **Frame Rate:** 30 fps

**Recording tip:** Hold your phone vertically and record in 1080p.

**What happens if your video doesn't meet these specs?**

The system will:
1. Detect it's invalid
2. Send you a Telegram message explaining what's wrong
3. Skip that video and move to the next one

---

**Your next step:** Open `01_Dropbox_Setup.md` to begin setup.

---

## Quick Reference

Once you're done, here's everything in one place:

### Platform Dashboard URLs
- **Dropbox Developer Console:** https://www.dropbox.com/developers/apps
- **Google Cloud Console:** https://console.cloud.google.com
- **YouTube Studio:** https://studio.youtube.com
- **Facebook Developer Portal:** https://developers.facebook.com
- **Instagram (via Facebook):** Uses same portal as Facebook
- **TikTok Developer Portal:** https://developers.tiktok.com

### Your n8n Instance
- **URL:** YOUR_N8N_PUBLIC_URL
- **OAuth Redirect URI (needed for all setups):**
  ```
  YOUR_N8N_PUBLIC_URL/rest/oauth2-credential/callback
  ```


---

**Document Version:** 1.0
**Created:** November 13, 2025
**For:** Eyal Dov
**Project:** Social Media Automation System
