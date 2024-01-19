<script>
  export let isAboutActive;

  let text1 = "Who am I";
  let textIndex1 = 0;
  let currentText1 = "";
  let typingSpeed = 200;

  function typeText1() {
    currentText1 = text1.substring(0, textIndex1 + 1);
    textIndex1++;
    setTimeout(typeText1, typingSpeed);
  }

  function startAnimations() {
    setTimeout(() => {
      typeText1();
    }, 1500);
  }

  $: if (isAboutActive) {
    startAnimations();
  }
</script>

<div class="container">
  <h2 class="whoami" class:text={isAboutActive && currentText1 != text1}>{currentText1}</h2>
  <svg id="first_line" class:active={isAboutActive} xmlns="http://www.w3.org/2000/svg" width="2023" height="205" viewBox="0 0 2023 205" fill="none">
    <g filter="url(#filter0_d_30_24)">
      <path d="M5.01057 194.702C170.787 129.305 293.974 83.4309 523.502 57C754.282 24.3761 1092.9 51.6061 1299.18 72.2612C1526 94.9732 1789.26 60.0159 2017.5 2.00004" stroke="url(#paint0_radial_30_24)" stroke-width="4" />
    </g>
    <defs>
      <filter id="filter0_d_30_24" x="0.251709" y="0.0640869" width="2021.77" height="204.497" filterUnits="userSpaceOnUse" color-interpolation-filters="sRGB">
        <feFlood flood-opacity="0" result="BackgroundImageFix" />
        <feColorMatrix in="SourceAlpha" type="matrix" values="0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 127 0" result="hardAlpha" />
        <feOffset dy="4" />
        <feGaussianBlur stdDeviation="2" />
        <feComposite in2="hardAlpha" operator="out" />
        <feColorMatrix type="matrix" values="0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0.25 0" />
        <feBlend mode="normal" in2="BackgroundImageFix" result="effect1_dropShadow_30_24" />
        <feBlend mode="normal" in="SourceGraphic" in2="effect1_dropShadow_30_24" result="shape" />
      </filter>
      <radialGradient id="paint0_radial_30_24" cx="0" cy="0" r="1" gradientUnits="userSpaceOnUse" gradientTransform="translate(165.057 276.121) rotate(-4.90837) scale(3074.93 816.886)">
        <stop stop-color="#423A9C" />
        <stop offset="0.09375" stop-color="#5746A5" />
        <stop offset="0.375" stop-color="#7E43A6" />
        <stop offset="0.697917" stop-color="#FF7F83" />
      </radialGradient>
    </defs>
  </svg>
  <svg id="second_line" class:active={isAboutActive} xmlns="http://www.w3.org/2000/svg" width="2191" height="252" viewBox="0 0 2191 252" fill="none">
    <path d="M2190 241C2032.99 257.582 2054.29 252.138 1768.5 198.578C1576 162.501 1446 136.575 1241.5 119.001C1049.5 102.501 782.376 209.182 579.625 198.578C376.874 187.974 170.139 122.324 2.00025 2.50181" stroke="url(#paint0_radial_7_3)" stroke-width="4" />
    <defs>
      <radialGradient id="paint0_radial_7_3" cx="0" cy="0" r="1" gradientUnits="userSpaceOnUse" gradientTransform="translate(2146.49 329.039) rotate(-164.8) scale(2596.27 916.185)">
        <stop stop-color="#FF7F83" />
        <stop offset="0.474206" stop-color="#7E43A6" />
        <stop offset="0.72619" stop-color="#5746A5" />
        <stop offset="1" stop-color="#423A9C" />
      </radialGradient>
    </defs>
  </svg>
</div>

<style lang="scss">
  .container {
    width: 1600px;
    margin: 0 auto;
    .whoami {
      margin-top: 200px;
      color: #fff;
      font-family: thinoo;
      font-size: 48px;
      font-style: normal;
      font-weight: 700;
      line-height: normal;
      margin-bottom: 0;
    }
    .aboutme {
      color: #d9d9d9;
      font-family: thinoo;
      font-size: 14px;
      font-style: normal;
      font-weight: 700;
      line-height: normal;
      margin: 0;
      margin-left: 8px;
    }
    .text::after {
      opacity: 0;
      content: "|";
      animation: blink 1s infinite 1.2s;
    }
  }

  #first_line {
    position: absolute;
    top: 0;
    left: 0;
    stroke-dashoffset: 200%;
    stroke-dasharray: 200%;
    transition: all 3s ease-in-out;
    transition-delay: 1s;
    &.active {
      stroke-dashoffset: 0%;
    }
  }
  #second_line {
    position: absolute;
    bottom: -40px;
    left: 0;
    stroke-dashoffset: 200%;
    stroke-dasharray: 200%;
    transition: all 3s ease-in-out;
    transition-delay: 1s;
    &.active {
      stroke-dashoffset: 0%;
    }
  }

  @keyframes blink {
    0% {
      opacity: 1;
    }

    50% {
      opacity: 0;
    }

    100% {
      opacity: 1;
    }
  }
</style>
