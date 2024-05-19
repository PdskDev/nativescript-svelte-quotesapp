<page>
    <actionBar>
      <label class="title" text="NadetDev Quote App"></label>
    </actionBar>
    <stackLayout class="home">
      <image src="~/images/image{imgNumber}.jpg"/>
      <textView text={message} class="quote" />
      <button text="Next Quote" on:tap="{onTap}" class="button"/>
    </stackLayout>
</page>

<script lang="ts">
    import { alert } from "@nativescript/core";

    let message: string = "Welcome to NadetDev Quote App";
    let min = 1;
    let max = 7;
    let imgNumber = 1;

    function randomImage(){
      imgNumber = Math.floor(Math.random() * (max - min)) + min;
    }

    $: imgNumber ? 1 : randomImage();

    //const onTap = ()=> alert('The button works good!');
    const onTap = ()=> randomImage();
</script>

<style>
    .home {
      background: #3aff96;
    }
    .title {
      font-weight: bold;
      font-size: 20px;
    }
    .quote {
      color: blue;
      font-size: 20rem;
      font-weight: 600;
      text-align: center;
    }
</style>
