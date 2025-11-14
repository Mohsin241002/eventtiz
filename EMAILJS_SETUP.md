# EmailJS Setup Guide for EventTiz

This guide will help you configure EmailJS to send event tickets via email.

## Step 1: Create an EmailJS Account

1. Go to [https://www.emailjs.com/](https://www.emailjs.com/)
2. Click "Sign Up" and create a free account
3. Verify your email address

## Step 2: Add an Email Service

1. Once logged in, go to **Email Services** in the dashboard
2. Click **Add New Service**
3. Choose your email provider (Gmail, Outlook, etc.)
4. Follow the instructions to connect your email account
5. **Copy the Service ID** - you'll need this for your `.env.local` file

## Step 3: Create an Email Template

1. Go to **Email Templates** in the dashboard
2. Click **Create New Template**
3. Use the following template structure:

### Template Variables to Include:
- `{{name}}` - Attendee's name
- `{{email}}` - Attendee's email
- `{{title}}` - Event title
- `{{date}}` - Event date
- `{{time}}` - Event time
- `{{description}}` - Event description
- `{{note}}` - Additional notes
- `{{passcode}}` - Unique ticket passcode
- `{{flier_url}}` - Event flier image URL

### Example Email Template:

**Subject:** Your Ticket for {{title}} 🎉

**Body:**
```
Hello {{name}},

Thank you for registering for {{title}}!

Here are your event details:

📅 Date: {{date}}
🕐 Time: {{time}}
📝 Description: {{description}}

🎫 Your Unique Ticket Passcode: {{passcode}}

{{note}}

Event Flier: {{flier_url}}

We look forward to seeing you at the event!

Best regards,
EventTiz Team
```

4. **Save the template** and copy the **Template ID**

## Step 4: Get Your Public API Key

1. Go to **Account** (top right corner)
2. Click on **API Keys**
3. Copy your **Public Key**

## Step 5: Update Your .env.local File

Open the `.env.local` file in your project root and replace the placeholder values:

```env
NEXT_PUBLIC_SERVICE_ID=service_xxxxxxx
NEXT_PUBLIC_TEMPLATE_ID=template_xxxxxxx
NEXT_PUBLIC_API_KEY=your_public_key_here
```

## Step 6: Restart Your Development Server

After updating the environment variables, restart your Next.js server:

```bash
# Stop the current server (Ctrl+C)
# Then restart it
npm run dev
```

## Testing

1. Go to your event registration page
2. Fill in the registration form
3. Submit the form
4. Check the registered email inbox for the ticket

## Troubleshooting

### Issue: Still getting stuck on "Generating your ticket"

**Solution:** Check the browser console (F12 > Console) for error messages. Common issues:
- Invalid Service ID, Template ID, or API Key
- Email service not properly connected
- Template variables don't match

### Issue: Email not received

**Solutions:**
- Check spam/junk folder
- Verify the email service is active in EmailJS dashboard
- Check EmailJS dashboard for email logs
- Ensure all template variables are correctly named

### Issue: "Failed to send ticket email" error

**Solutions:**
- Verify your EmailJS account is active
- Check if you've exceeded the free tier limit (200 emails/month)
- Ensure your email service is properly authenticated

## EmailJS Free Tier Limits

- 200 emails per month
- 2 email services
- 2 email templates

If you need more, consider upgrading to a paid plan.

## Additional Resources

- [EmailJS Documentation](https://www.emailjs.com/docs/)
- [EmailJS Dashboard](https://dashboard.emailjs.com/)

