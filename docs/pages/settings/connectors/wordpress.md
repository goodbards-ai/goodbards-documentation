# WordPress (self-hosted)

Send your blog posts to your own WordPress website, and bring your existing
articles into GoodBards.

## What it's for

Use this connector if your website runs on WordPress that you or your agency host
(not on WordPress.com — for that, see [WordPress.com](wordpress-com.md)). With it
you can:

- **Send blog posts to WordPress** from a campaign's **Blog Post** tactic. See
  [Launch a tactic](../../marketing/launch-tactic.md).
- **Import your existing articles** into the Content Repository with **+ New →
  Import WordPress**, so the AI can learn from what you already published. See
  [Content Repository](../../workspace/drive.md).

## Before you start

- You must be an **administrator** or the **owner** of your GoodBards company
  account.
- You need a WordPress user that can write posts and upload media.
- Create an **Application Password** for that user in WordPress: in your
  WordPress admin, open **Users → Profile**, then **Application Passwords**.
  It is not your normal login password.
- Your site's WordPress REST API must be reachable (at
  `https://yoursite.com/wp-json`). Some security plugins switch it off.

## How to connect

1. Open your account menu (your picture, top right), then choose **Connections**.
2. On the **CMS** tab, find **Wordpress (Self Hosted)** and choose **Connect**.
3. Fill in:
    - **Website URL**: your site's address, for example `https://yoursite.com`.
    - **Username**: the WordPress user name.
    - **Application Password**: the application password you created.
4. Choose **Save Settings**.

## What GoodBards does with it

| GoodBards… | Details |
| --- | --- |
| **Creates** | A **draft** post with your title and content. The first picture is uploaded and becomes the featured image. |
| **Deletes** | The post, when you remove it from GoodBards. Uploaded pictures stay in your media library. |
| **Reads** | Your existing posts (for the import) and the post types you can publish to. |

## Good to know

- **Posts arrive as drafts.** Review them in WordPress and publish from there.
- **Pick the post type as destination.** When you publish, GoodBards lists the
  post types your site offers.

## How to disconnect

1. On the Wordpress (Self Hosted) card, choose **Disconnect**.
2. Confirm.

Drafts already sent stay in WordPress. You can also revoke the application
password in WordPress.

---

*Still stuck? [Contact support](../../contact.md).*
