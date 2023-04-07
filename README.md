# 100 Days Diary

100 Days Diary is a web app that allows you to keep a diary of your thoughts and experiences for up to 100 days. It also uses AI to analyze your diary entries and provide summaries of your mood and other statistics for the past 100 days.

## Usage

To use the app, simply open the index.html file in a web browser. You can then add new diary entries by clicking the "Add Entry" button and filling out the form. Each entry can include text, photos, and voice notes. The app will automatically store the last 100 days of entries and upload older data to the cloud for backup.

To view a summary of your mood and other statistics for the past 100 days, click the "Summary" button in the top right corner of the screen. The app will display a mood strip that shows the average mood over the past 100 days, as well as a list of the number of entries for each mood level.

## Development

To develop the app, you will need to have Node.js and npm installed on your computer. First, clone the repository and navigate to the project directory in your terminal. Then, run the following commands to install the necessary dependencies and start the development server:

```shell
npm install
npm run dev
```

This will start a local development server at http://localhost:5000. You can make changes to the app code in the src directory and see them reflected in the browser.

To build the app for production, run the following command:


```shell
npm run build
```


This will generate a production-ready version of the app in the public directory. You can then deploy this directory to a web server to make the app available online.

## License

This project is licensed under the MIT License. See the LICENSE file for details.