<script>
  import { onMount } from "svelte";
  import PaperPlane from "../assets/svg/paperPlane.svelte";
  import Notebook from "../assets/svg/notebook.svelte";
  let text1 = "HELLO, I’M";
  let text2 = ["MARTIN KUBANDA", "FULL STACK DEVELOPER"];
  let textIndex1 = 0,
    textIndex2 = 0,
    index = 0;
  let currentText1 = "",
    currentText2 = "";
  let typingSpeed = 200;
  let isDeleting = false;

  function typeText1() {
    currentText1 = text1.substring(0, textIndex1 + 1);
    textIndex1++;
    currentText1 == text1 ? setTimeout(typeText2, 1000) : setTimeout(typeText1, typingSpeed);
  }

  function typeText2() {
    const fullTxt = text2[index];
    if (isDeleting) {
      currentText2 = fullTxt.substring(0, currentText2.length - 1);
    } else {
      currentText2 = fullTxt.substring(0, textIndex2 + 1);
    }
    let typingSpeed = 200;
    if (isDeleting) typingSpeed /= 2;
    if (!isDeleting && currentText2 === fullTxt) {
      typingSpeed = 1000;
      isDeleting = true;
    } else if (isDeleting && currentText2 === "") {
      isDeleting = false;
      index = (index + 1) % text2.length;
      textIndex2 = 0;
    }
    if (!isDeleting) textIndex2++;
    setTimeout(typeText2, typingSpeed);
  }
  onMount(() => {
    setTimeout(typeText1, 1000);
  });
</script>

<div class="container">
  <svg id="headerLine" xmlns="http://www.w3.org/2000/svg" width="1920" height="681" viewBox="0 0 1920 681" fill="none">
    <path d="M-74.8811 678.135C-17.7525 678.135 50.8593 434.915 192.825 364.837C338.734 294.759 447.164 292.645 593.073 257.606C735.038 222.567 917.537 93.0608 1063.45 -12.056C1205.41 -117.173 1331.08 -12.4037 1476.99 22.6352C1618.96 57.6742 1796.8 27.3696 1942.71 -7.66935" stroke="url(#paint0_radial_7_5)" stroke-width="4" />
    <defs>
      <radialGradient id="paint0_radial_7_5" cx="0" cy="0" r="1" gradientUnits="userSpaceOnUse" gradientTransform="translate(79.0582 621.081) scale(1844.08 1183.12)">
        <stop stop-color="#FF7F83" />
        <stop offset="0.474206" stop-color="#7E43A6" />
        <stop offset="0.72619" stop-color="#5746A5" />
        <stop offset="1" stop-color="#423A9C" />
      </radialGradient>
    </defs>
  </svg>
  <svg id="headerLineBottom" xmlns="http://www.w3.org/2000/svg" width="1918" height="130" viewBox="0 0 1918 130" fill="none">
    <path d="M1.16003 106.546C14.3685 102.432 240.722 16.3917 350.441 4.28787C462.654 -7.81599 554.743 39.9745 666.956 76.2861C776.675 112.598 888.888 136.805 998.607 124.701C1108.33 112.597 1189.91 24.9524 1299.63 24.9524C1411.84 24.9524 1552.19 112.597 1664.4 124.701C1774.12 136.805 1886.33 112.598 1941.19 100.494" stroke="url(#paint0_radial_15_10)" stroke-width="4" />
    <defs>
      <radialGradient id="paint0_radial_15_10" cx="0" cy="0" r="1" gradientUnits="userSpaceOnUse" gradientTransform="translate(-608.047 187.854) scale(2548.8 325.803)">
        <stop offset="0.479167" stop-color="#FF7F83" />
        <stop offset="0.796875" stop-color="#5746A5" />
        <stop offset="1" stop-color="#423A9C" />
      </radialGradient>
    </defs>
  </svg>
  <div class="header">
    <h3>kubanda.m</h3>
    <svg id="menuButton" xmlns="http://www.w3.org/2000/svg" width="46" height="44" viewBox="0 0 46 44" fill="none">
      <rect id="rect1" x="10.6282" y="13.0487" width="34.0026" height="5.52949" rx="2.76475" stroke="white" />
      <rect id="rect2" x="0.627441" y="25.1749" width="44.0033" height="5.52949" rx="2.76475" stroke="white" />
      <rect id="rect3" x="20.629" y="37.3011" width="24.0019" height="5.52949" rx="2.76475" stroke="white" />
      <rect id="rect4" x="0.627319" y="0.922516" width="44.0033" height="5.52949" rx="2.76475" stroke="white" />
    </svg>
  </div>
  <div class="center_content">
    <h1 class:text={currentText1 != text1}>{currentText1}</h1>
    <h1 class:text={currentText1 == text1}>{currentText2}</h1>
  </div>
  <PaperPlane id="paperPlane" />
  <Notebook id="notebook" />
</div>

<style lang="scss">
  #headerLine {
    position: absolute;
    top: 0;
    left: 0;
    stroke-dashoffset: 200%;
    stroke-dasharray: 200%;
    animation: drawLine 4s forwards;
  }
  #headerLineBottom {
    position: absolute;
    bottom: 0;
    left: 0;
    stroke-dashoffset: 200%;
    stroke-dasharray: 200%;
    transform: scale(-1);
    animation: drawLine 6s forwards;
  }

  .container {
    width: 1600px;
    margin: 0 auto;
  }

  .center_content {
    margin-top: 300px;

    h1 {
      color: #d9d9d9;
      font-family: thinoo;
      font-size: 70px;
      font-style: normal;
      font-weight: 100;
      line-height: normal;
      opacity: 0;
      animation: fadeIn 1s forwards 1s;
    }

    .text::after {
      opacity: 0;
      content: "|";
      animation: blink 1s infinite;
    }
  }

  .header {
    margin-top: 60px;
    display: flex;
    align-items: center;
    justify-content: space-between;

    h3 {
      color: #fff;
      font-family: thinoo;
      font-size: 48px;
      font-style: normal;
      font-weight: 100;
      line-height: normal;
      animation: slideFromLeft 2s forwards; // adjust duration as needed
    }

    svg#menuButton {
      cursor: pointer;
      animation: slideFromRight 2s forwards;
    }
  }

  @keyframes drawLine {
    0% {
      stroke-dashoffset: 200%;
    }

    100% {
      stroke-dashoffset: 0;
    }
  }

  @keyframes slideFromLeft {
    0% {
      transform: translateX(-2000px);
    }

    100% {
      transform: translateX(0);
    }
  }

  @keyframes slideFromRight {
    0% {
      transform: translateX(2000px);
    }

    100% {
      transform: translateX(0);
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

  @keyframes fadeIn {
    0% {
      opacity: 0;
    }

    100% {
      opacity: 1;
    }
  }
</style>
