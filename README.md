# 📱 Google Sheets SMS Sender

A powerful Google Apps Script that enables sending SMS messages directly from Google Sheets using the MRAM API. Features individual send buttons for each row, real-time status tracking, and automatic retry functionality.

## ✨ Features

- **Individual SMS Buttons**: Click-to-send button for each row in Column F
- **Real-time Status Updates**: Live status tracking in Column E
- **Smart Retry System**: Automatically retry failed messages
- **SMS ID Extraction**: Clean extraction of SMS IDs from API responses
- **Delivery Status Tracking**: Check delivery status for sent messages
- **Balance Monitoring**: Check remaining SMS balance
- **Visual Feedback**: Color-coded status indicators
- **Error Handling**: Robust error handling with detailed feedback

## 🏗️ Sheet Structure

| Column | Purpose | Example |
|--------|---------|---------|
| A | Phone Number | `+8801712345678` |
| B | Message | `Hello! This is a test message.` |
| C | SMS ID | `bw-rdC3000708689add11452c1` |
| D | Delivery Status | `DELIVERED` |
| E | Status | `✅ Sent` |
| F | Send Button | `📤 SEND` |

## 🚀 Quick Start

### 1. Setup Google Apps Script

1. Open [Google Sheets](https://sheets.google.com)
2. Create a new spreadsheet
3. Go to **Extensions** → **Apps Script**
4. Delete the default code and paste the code from `sms-script.gs`
5. Save the project (Ctrl+S)

### 2. Configure API Credentials

Update these lines in the script with your MRAM credentials:
```javascript
var API_KEY = "YOUR_API_KEY";      // Replace with your MRAM API Key
var SENDER_ID = "YOUR_SENDER_ID";  // Replace with your approved Sender ID
```

### 3. Setup Click Triggers

1. In Apps Script, click **Triggers** (⏰ icon)
2. Click **+ Add Trigger**
3. Configure:
   - **Function**: `onSelectionChange`
   - **Event source**: From spreadsheet
   - **Event type**: On change
4. Click **Save**

### 4. Initialize Sheet

1. Go back to your Google Sheet
2. Click **📩 SMS Menu** → **Setup Buttons**
3. Your sheet is now ready!

## 🎯 How to Use

### Sending SMS

1. **Fill Data**: Add phone numbers in Column A and messages in Column B
2. **Click Send**: Click the blue **📤 SEND** button in Column F for any row
3. **Monitor Status**: Watch Column E for real-time status updates

### Button States

| Button | Status | Description |
|--------|--------|-------------|
| 🔵 **📤 SEND** | Ready | Click to send SMS |
| 🟠 **⏳ SENDING...** | Processing | SMS being sent |
| 🟢 **✅ SENT** | Success | SMS sent successfully |
| 🔴 **🔄 RETRY** | Failed | Click to retry sending |

### Menu Options

Access these features from **📩 SMS Menu**:

- **Send All SMS**: Send all unsent messages at once
- **Check Delivery Status**: Check delivery status for sent messages
- **Check Balance**: View remaining SMS balance
- **Setup Buttons**: Initialize/reset button layout
- **Send SMS for Selected Row**: Send SMS for currently selected row

## 🔧 Advanced Configuration

### Custom SMS ID Extraction

The script automatically extracts SMS IDs from responses like:
```
SMS SUBMITTED: ID - bw-rdC3000708689add11452c1
```
↓ Extracts ↓
```
bw-rdC3000708689add11452c1
```

### Error Handling

Failed messages will show detailed error information and keep the SMS ID cell empty for easy retry.

### Bulk Operations

Use **Send All SMS** to process multiple rows automatically, skipping already sent messages.

## 📋 MRAM API Integration

This script integrates with the MRAM SMS API endpoints:

- **Send SMS**: `https://sms.mram.com.bd/smsapi`
- **Check Delivery**: `https://sms.mram.com.bd/miscapi/{API_KEY}/getDLRRep/{SMS_ID}`
- **Check Balance**: `https://sms.mram.com.bd/miscapi/{API_KEY}/getBalance`

## 🛡️ Security Best Practices

1. **Never commit API keys** to public repositories
2. **Use environment variables** for sensitive data in production
3. **Regularly rotate API keys**
4. **Monitor API usage** to prevent abuse

## 🐛 Troubleshooting

### Common Issues

**Issue**: Button doesn't work when clicked
- **Solution**: Ensure the `onSelectionChange` trigger is properly set up

**Issue**: "❌ Failed" status but no error details
- **Solution**: Check your API credentials and internet connection

**Issue**: SMS ID not extracted properly
- **Solution**: Verify the API response format matches the extraction pattern

**Issue**: Can't retry failed messages
- **Solution**: The script automatically allows retry for failed messages

### Debug Mode

To enable detailed logging:
1. In Apps Script, go to **View** → **Logs**
2. Add `console.log()` statements in the script for debugging

## 📞 Support

For issues related to:
- **MRAM API**: Contact MRAM support
- **Google Apps Script**: Check [Google Apps Script documentation](https://developers.google.com/apps-script)
- **This Script**: Create an issue in this repository

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🤝 Contributing

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## 📈 Changelog

### v1.0.0
- Initial release with basic SMS sending functionality
- Individual row send buttons
- Status tracking and retry functionality
- MRAM API integration
- Delivery status checking
- Balance monitoring

## ⭐ Show Your Support

If this project helped you, please give it a ⭐ star!

---

**Made with ❤️ for the Google Sheets community**
