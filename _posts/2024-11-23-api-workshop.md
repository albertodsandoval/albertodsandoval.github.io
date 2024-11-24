---
title: "What is an API? How can I use one?"
date: 2024-11-23
categories:
  - Blog
tags: 
  - Lesson
  - APIs
  - Workshop
---

> In this blog post, I will quickly explain some
> of the concepts discussed at **CSUN's** _Girl's Who Code_
> hosted API workshop featuring **Luis J Guzman**,
> a web developer at **CSUN**.

## The history of APIs

To start us off, Guzman briefly went over the history
of, well the **_internet_**. Trying to build our intuition
on the **idea** of APIs. To sum up everything
he explained:
> The entire internet is built on one idea,
> file sharing. Companies have grown to make 
> businesses out of this simple idea but 
>  the internet simply acts as a way to access,
> exchange, and share files with others globally.

This idea did intrigue me quite a bit since it gave me 
a new perspective on something I am already familiar with.
Websites don't literally give you anything, at the end
of the day the internet and all of its contents are 
merely 1s and 0s. But given a file with exclusivity
or one that requires a trade-off, one may receive 
benefits beyond the digital world. This is the internal
philosophy behind things like online shopping. But
in what way does this relate to APIs? Well, this whole 
spiel about the philosophy of the internet does relate 
to APIs in one simple way: APIs simply allow for websites
to access files.

## So... what is an API?

The acronym API stands for Application Programming Interface.
What it does is allow programs that don't have data or **_files_**
built in to them to access files stored somewhere else on the internet,
usually in a database. For example, a user accessing a website like YouTube
doesn't need to have every single video ever uploaded to YouTube
installed on their phone or computer. The YouTube application uses
an API to fetch the information on a video, which exists elsewhere. 
If this location, the one that actually contains the video, is accessible
to the public, than anyone can make a website similar to YouTube that 
streams the same videos that YouTube does.  

To explain it using an analogy, 
imagine a vinyl record store owner that has a huge inventory of records.
Struggling to get people to purchase from his store, he instead offers a 
new service. For a price, individuals can call the record store and listen
to their favorite album over the phone. If another individual had access
to the same library of records, they too can offer the service of playing
albums for customers over the phone. In this analogy, the service of 
playing the record is the API and the phone line would be the internet.  

You can see how this analogy also ties into the idea that the entire 
internet is just file sharing, and that APIs are what grant applications
the ability to share files to an individual who doesn't have them. The API
acts as an intermediary between the individual or program that doesn't 
have the files or data, and the one the does.

## Applications of APIs

Guzman did show us a few examples of what an API could look like 
in an application: a random cat image generator, a random inspiring
quote generator, as well as a weather API that displays the weather for our location.
This, of course, is just a few examples that show situations APIs can be used in.
Generally, APIs are used in almost every website or application. Nearly every
instance where you press a button or trigger an event and something loads 
up without transferring you to another URL is likely the work of an API.  

In all of these situations, the website (or application) running the 
code understands the instructions the programmer is giving it. This is
the massive benefit of JavaScript, it allows code to be run on the clients
side. And for those tuning in that have zero experience with coding, most
programs require that you have a certain language and/or toolset installed on 
your computer to run. There are many _dependencies_ that code usually relies
on, but browsers impressively understand JavaScript and can run 
it out the box. This allows programmers the ability to leave a lot of the
code execution to the user trying to access it, revolutionary.

## But what does an API look like in code?

Well... an API can be coded up in nearly any language, so it's hard to 
show syntactically what it would look like. But this, for example, is
a chunk of code calling [The Cat API](https://thecatapi.com/).


```js
<button onclick="fetchCat();">
Click for cat!
</button>
<div id="cat-container"></div>

<script>
  async function fetchCat() {
    const response = await fetch('https://api.thecatapi.com/v1/images/search');
    const data = await response.json();
    const catImage = data[0].url;


    // Create an image element and add it to the container
    const imgElement = document.createElement('img');
    imgElement.src = catImage;
    imgElement.alt = "A random cat";
    imgElement.style.maxWidth = "100%"; // Ensure the image fits nicely

    const container = document.getElementById('cat-container');
    container.innerHTML = "";
    container.appendChild(imgElement);
  }
</script>
```

And here is a fully functioning API call injected right into this very blog post

<button onclick="fetchCat();">
    Click for cat!
</button>
<div id="cat-container"></div>
<script>
  async function fetchCat() {
    const response = await fetch('https://api.thecatapi.com/v1/images/search');
    const data = await response.json();
    const catImage = data[0].url;
    // Create an image element and add it to the container
    const imgElement = document.createElement('img');
    imgElement.src = catImage;
    imgElement.alt = "A random cat";
    imgElement.style.maxWidth = "100%"; // Ensure the image fits nicely
    const container = document.getElementById('cat-container');
    container.innerHTML = "";
    container.appendChild(imgElement);
  }
</script>

The link <https://api.thecatapi.com/v1/images/search> is an API endpoint, 
and it returns an Object that contains the URL of an image of a cute cat. On _The Cat APIs_
website, they provide an example of what one of these objects might look like
, so from here it is easy to figure out how to extract the URL. 
This is the Object example provided by _The Cat API_:
```json
[{
    "id":"ebv",
    "url":"https://cdn2.thecatapi.com/images/ebv.jpg",
    "width":176,"height":540,
    "breeds":[],
    "favourite":{}
}]
```
We know that there is a field in this Object called "url" that contains the url of a cat image.
So we can create some code that:
1. Creates a button element to click
    * this button will call _fetchCat_ when pressed
2. Creates a div element to hold the image when we get it
3. Defines the function _fetchCat_ which is called by the button
4. _fetchCat_ then reaches out to the API and saves the object in _response_
    * _response_ is then converted to JSON and saved in _data_
      * JSON is JavaScript Object Notation, and it is essentially a format that JavaScript recognizes
5. We create an image that displays the image located at the URL in the Object retrieved from the API
6. We insert that image into the div we created earlier

## Conclusion

And just like that, an API call! Many useful APIs exist out there that you can use
in your applications. And the neat thing about programming is, if what you are looking
for doesn't exist, you can make it yourself! Now that is a challenge a little more intense
than simply calling an existing API, but stick with me through this educational journey, stay
consistent, love the process, and one day things like this will be a breeze. Cheers to my 
first blog post, I finally did it!

Anyway, feel free to leave any corrections or suggestions on topics you may want me to cover
in my email inbox, and I will be sure to get to them as soon as possible. Thank you so much for
reading, I truly hope that this was informative or at least interesting. Stay tuned for more coming
soon!

