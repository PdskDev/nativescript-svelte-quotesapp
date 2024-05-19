<page>
    <actionBar>
      <label class="title" text="NadetDev Quote App"></label>
    </actionBar>
    <scrollView orientation='vertical'>
      <stackLayout class="home">
        <image src="~/images/image{imgNumber}.jpg" class="img"/>
        <textView text={quote} class="quote" />
        <label class="info">
          <formattedString>
            <span text="{author}" class="author" />
          </formattedString>
        </label>
        <button text="Next Quote" on:tap="{onTap}" class="button"/>
      </stackLayout>

    </scrollView>

</page>

<script lang="ts">
    //import { alert } from "@nativescript/core";
    import { quotesList } from "~/model/quoteList";

    //let message: string = "Welcome to NadetDev Quote App";
    let min = 1;
    let max = 7;
    let imgNumber = 1;
    let quote: string;
    let author: string;

    function randomImage(){
      imgNumber = Math.floor(Math.random() * (max - min)) + min;
    }

    $: imgNumber ? 1 : randomImage();

    //const onTap = ()=> alert('The button works good!');
    //const onTap = ()=> randomImage();

    function randomQuote(){
      let i = Math.floor(Math.random() * quotesList.length);
      quote = quotesList[i].quote;
      author = quotesList[i].author
      return [quote, author];
    }

    function randomItems(){
      randomImage();
      randomQuote();
    }

    const onTap = ()=> randomItems();
</script>

<style>
    .home {
      background: rgb(105,134,14);
      background: linear-gradient(90deg, rgba(105,134,14,1) 0%, rgba(121,161,91,1) 100%);
    }
    .title {
      font-weight: bold;
      font-size: 20px;
    }
    .quote {
      color: #24261c;
      font-size: 30rem;
      font-weight: 600;
      text-align: center;
      margin-top: 10px;
      margin-bottom: 10px;
    }
    .author {
      color: #24261c;
      font-size: 20rem;
      font-weight: 400;
      text-align: center;
      margin-top: 10px;
      margin-bottom: 10px;
    }
    .info{
      text-align: center;
    }
    .button{
      background: rgb(220, 162, 219);
      background: linear-gradient(90deg, rgba(220,162,219,1) 15%, rgba(75,83,174,1) 100%);
      color: #24261c;
      font-size: 20rem;
      border-radius: 0 20px;
    }
    .img {
      border-radius: 0 50px;
      margin: 20px;
      border: solid 5px #24261c;
    }
</style>
