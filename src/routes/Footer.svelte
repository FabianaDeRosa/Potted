<script>
  import { onMount } from "svelte";
  import Fa from "svelte-fa";
  import { faInstagram } from "@fortawesome/free-brands-svg-icons";
  import { faTwitter } from "@fortawesome/free-brands-svg-icons";
  import { faPinterest } from "@fortawesome/free-brands-svg-icons";
  import Logo from "$lib/images/icons/logo.svg";
  import FooterSketch from "./FooterSketch.svelte";

  let fot;
  let scroll = false;

  onMount(() => {
    const footer = document.getElementById("footer");

    const handleScroll = () => {
      const rect = footer.getBoundingClientRect();
      scroll = rect.top <= window.innerHeight && rect.bottom >= 0;
    };

    window.addEventListener("scroll", handleScroll);

    //check se il footer è in vista quando carico la pagina
    handleScroll();

    // Rimozione dell'event listener quando il componente viene smontato
    return () => {
      window.removeEventListener("scroll", handleScroll);
    };
  });
</script>

<svelte:window bind:innerHeight={fot} />


<footer id="footer">
    <img id="logo-icon" src={Logo} alt="Potted logo"/>
    <span>A space for plant and pottery lovers.</span>
    <p><span>Sign up</span> with your email address to receive our latest news and updates.</p>
    <input type="email" id="email" name="email" placeholder="Your email">
    <button class="subsc-btn">Subscribe</button>
    <div class="social-icons">
        <a href="/"><button><Fa icon={faInstagram} size="2x" color="#FDF8F1" /></button></a>
        <a href="/"><button><Fa icon={faTwitter} size="2x" color="#FDF8F1" /></button></a>
        <a href="/"><button><Fa icon={faPinterest} size="2x" color="#FDF8F1" /></button></a>
    </div>
    <div class="info">
        <a href="/">Privacy Policy</a>
        <a href="/">FAQ & Delivery</a>
    </div>
    {#if scroll}
    <div id="p5-footer">
      <FooterSketch/>
    </div>
    {/if}
</footer>



<style lang="scss">

    #p5-footer{
      position: absolute;
      top: 0;
    }

    footer {
      padding-top: 4rem;
      background-color: map-get($colors, dark);
      display: grid;
      grid-template-rows: min-content;
      place-items: center;
      position: relative;
  
      #logo-icon {
        width: 15ch;
        filter: invert(1);
      }
  
      span {
        margin: 0;
        color: map-get($colors, primary);
      }
  
      p {
        color: map-get($colors, primary);
        font-weight: 200;
        margin-bottom: 0;
        font-size: 1.1rem;
        margin-top: 4rem;
        text-align: center;
  
        span {
          color: map-get($colors, clay);
        }
      }
  
      input {
        padding: .5rem;
        padding-right: 8rem;
        margin: 1rem;
        z-index: 1;
      }
  
      button {
        background: none;
        cursor: pointer;
        border: none;
        z-index: 1;
      }
  
      .subsc-btn {
        @include btn-style;
        color: map-get($colors, primary);
        border: solid 2px map-get($colors, primary);
        margin-bottom: 5rem;
        font-size: 1rem;
        margin-top: 0;
        background-color: map-get($colors, dark);
        
        &:hover {
          background-color: map-get($colors, beige);
          color: map-get($colors, dark);
        }
      }
  
      .info {
        margin-top: 1rem;
  
        a {
          color: map-get($colors, primary);
          font-size: .7rem;
          font-weight: 200;
  
          &:hover {
            color: map-get($colors, clay);
          }
        }
      }
    }
  </style>
  
