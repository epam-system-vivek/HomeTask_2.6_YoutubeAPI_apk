https://www.googleapis.com/youtube/v3/search?key=AIzaSyDyEJJtRT1ZJIZTACqqmC-YczJon-K1weo&pageToken=CA8QAA&type=video&part=snippet&maxResults=15&q=javascript

https://www.googleapis.com/youtube/v3/search?key=AIzaSyD69yDcPC-xKwVgBKOZ_lbeRxGr3RzmrhY&type=video&part=snippet&maxResults=15&q=telsusko

https://console.cloud.google.com/apis/credentials/key/69c59880-1f85-4289-a6a6-a23f8f7d54db?project=youtubeapp-378105&supportedpurview=project

youtube link: https://www.youtube.com/watch?v=JbWnRhHfTDA

https://console.cloud.google.com/apis/credentials?project=youtubeapi-378506





Task: Create web-application for load and search info about YouTube videos using user's request.

Use-case:
1. User opens the application and see search input

2. User types the topic inside of search input. For example javascript

3. Application makes call to YouTube REST API and shows results as thumbnails in horizontal list

4. List is scrolled through click on the page. Video count on the page depends on screen size. 

5. Load 15 records, the rest if the records that doesn't in the screen will go into pagination.
 The page numbers will be below the thumbnails.

Requirements:
1. Chrome support and one mobile platform

2. HTML creates using JS. Almost no code inside index.html.

3. No jquery or other frameworks. You can use only lodash.

4. JS code should be splitted to different files depending on architecture.

5. Minimal info about video is title with link on youtube, preview, description, author,
     published date, count of views.

6. Data from youtube could be received using:
- https://www.googleapis.com/youtube/v3/search?key=AIzaSyCTWC75i70moJLzyNh3tt4jzCljZcRkU8Y&type=video&part=snippet&maxResults=15&q=js
- https://www.googleapis.com/youtube/v3/videos?key=AIzaSyCTWC75i70moJLzyNh3tt4jzCljZcRkU8Y&id=nq4aU9gmZQk,REu2BcnlD34,qbPTdW7KgOg&part=snippet,statistics
- how too receive API key - https://www.youtube.com/watch?v=JbWnRhHfTDA
- full documentation - https://developers.google.com/youtube/v3/

7. Design should be not ugly


unit testcases
// Test case for fetchData function
test('fetchData function should return a promise that resolves with data when passed a valid URL', async () => {
  const data = await fetchData('https://example.com');
  expect(data).toBeDefined();
});

test('fetchData function should reject the promise when passed an invalid URL', async () => {
  await expect(fetchData('https://nonexistentwebsite.com')).rejects.toThrow();
});

// Test case for fetchVideos function
test('fetchVideos function should return an array of video objects when passed a valid search query', async () => {
  const videos = await fetchVideos('cats');
  expect(Array.isArray(videos)).toBe(true);
  expect(videos.length).toBeGreaterThan(0);
});

test('fetchVideos function should reject the promise when passed an invalid search query', async () => {
  await expect(fetchVideos('')).rejects.toThrow();
});

// Test case for renderVideos function
test('renderVideos function should add video thumbnails to the DOM', () => {
  document.body.innerHTML = '<div id="thumbnails"></div>';
  const videos = [    { id: 'video1', thumbnail: 'https://example.com/image1.jpg' },    { id: 'video2', thumbnail: 'https://example.com/image2.jpg' },  ];
  renderVideos(videos);
  const thumbnails = document.querySelectorAll('#thumbnails .thumbnail');
  expect(thumbnails.length).toBe(videos.length);
});