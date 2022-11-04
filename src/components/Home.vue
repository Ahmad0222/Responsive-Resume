<!-- eslint-disable vue/multi-word-component-names -->
<template>
  <div class="main_noti" id="notification">
    <div class="notification" :class="this.$data.notification.type">
      <div class="title">{{ this.$data.notification.title }}</div>
      <p>{{ this.$data.notification.message }}</p>
      <span class="progress"></span>
    </div>
  </div>
  <div class="keyo_main">
    <div class="logo">
      <img src="../assets/keyoLogo.webp" alt="" class="keyo_logo" />
    </div>
    <div>
      <div class="keyo_row">
        <div class="keyo_card" style="position: relative">
          <div class="heading">System Population</div>
          <p class="description">
            The system population equals the total number of users between 1 and 100 million Keyo has in the server or ID Vault.
          </p>
          <form @submit="numMat" style="margin-bottom: 0.5rem">
            <input
              type="text"
              v-model="numUsers"
              class="keyo_input"
              placeholder="ex. 10,000,000"
              required
              id="numberUsers"
              maxlength="11"
            />
            <button type="submit" class="keyo_button">Create Demo Users</button>
          </form>
          <table class="matchServer" id="matchServer">
            <tr>
              <td>
                <span>(Matching Engine Instances)</span> <br />
                Servers Provisioned:
              </td>
              <td style="padding-left: 6rem; padding-right: 0.5rem;">Servers : {{ this.$data.ListValue }}</td>
            </tr>
          </table>
          <button
            type="button"
            class="keyo_button reset_button"
            style="width: 40%; position: absolute; bottom: 50px; left: 15px"
            @click="deleteUsers"
          >
            Reset System
          </button>
        </div>
        <div class="keyo_card">
          <div class="heading">Matching</div>
          <p class="description">
            The number of match requests based on users you want to match at once or in a relatively short time.
          </p>
          <form @submit="onSubmit">
            <label class="keyo_label">Match Requests</label>
            <input
              type="text"
              class="keyo_input"
              required
              placeholder="ex. 10,000,000"
              v-model="numMatches"
              id="numberMatches"
              maxlength="7"
            />
            <label class="keyo_label">Target Throughput</label>
            <select
              v-model="NumMatchRate"
              class="keyo_input throughput"
              required
            >
              <option disabled value="">Set Frequency</option>
              <option>160</option>
              <option>320</option>
              <option>480</option>
              <option>640</option>
            </select>
            <button
            style="width: 40%;"
              class="keyo_button disabled"
              disabled
              type="submit"
              id="keyo_start"
            >
              Start
            </button>
          </form>
        </div>
        <div class="keyo_card">
          <div class="heading">Output</div>
          <p class="description">
            Benchmark visualizations based on the results of Keyo's ID vault. Successful outputs include Identification Average Latency, Identification Max Latency, Identification Throughput, and Elapsed time.
          </p>
          <table>
            <tr>
              <td>
                <span>(MILLISECONDS)</span> <br />
                Identification Average Latency:
              </td>
              <td class="keyo_td">{{ this.$data.InitialData.summary.latency_avg }} ms</td>
            </tr>
            <tr>
              <td>
                <span>(MILLISECONDS)</span> <br />Identification Max Latency:
              </td>
              <td class="keyo_td">{{ this.$data.InitialData.summary.latency_max }} ms</td>
            </tr>
            <tr>
              <td>
                <span>(MATCHES / SECONDS)</span> <br />Identification
                Throughput:
              </td>
              <td class="keyo_td">{{ this.$data.InitialData.summary.throughput_avg }}</td>
            </tr>
            <tr>
              <td><span>(MILLISECONDS)</span> <br />Elapsed Time:</td>
              <td class="keyo_td">{{ this.$data.InitialData.summary.run_time }} ms</td>
            </tr>
          </table>
        </div>
      </div>
      <div class="keyo_output">
        <div class="output_card">
          <div class="output_left">
            <div class="main_icon" id="server_icon">
              <svg
                
                class="keyo_wave"
                viewBox="0 0 193 193"
                fill="none"
                xmlns="http://www.w3.org/2000/svg"
              >
                <circle cx="96.5" cy="96.5" r="78.5" fill="#111111" />
                <g filter="url(#filter0_f_6_848)">
                  <circle
                    cx="96.4994"
                    cy="96.5001"
                    r="76.3819"
                    fill="url(#paint0_linear_6_848)"
                  />
                </g>
                <circle cx="96.4513" cy="96.5" r="63.1442" fill="#2C2C2C" />
                <path
                  fill-rule="evenodd"
                  clip-rule="evenodd"
                  d="M76.0913 52.9323C76.0913 49.0466 79.2706 45.8673 83.1563 45.8673C87.0421 45.8673 90.2213 49.0466 90.2213 52.9323C90.2213 56.8181 87.0421 59.9973 83.1563 59.9973C79.2706 59.9973 76.0913 56.8181 76.0913 52.9323ZM76.9747 52.9322C76.9747 56.3587 79.73 59.1141 83.1566 59.1141C86.5478 59.1141 89.3384 56.3587 89.3384 52.9322C89.3384 49.5057 86.5831 46.7503 83.1566 46.7503C79.73 46.7503 76.9747 49.5057 76.9747 52.9322Z"
                  fill="#F9F9F9"
                />
                <path
                  d="M81.708 50.4248L82.026 50.7074L82.6618 50.0715L82.2026 49.6476C81.92 49.4003 81.5314 49.259 81.1428 49.259C80.2597 49.259 79.5532 49.9655 79.5532 50.8487V54.9817C79.5532 55.6529 79.9418 56.2887 80.5776 56.536C81.1782 56.7833 81.8493 56.6066 82.2732 56.1827L84.4987 53.9219L83.8982 53.2861L81.7434 55.4409C81.2488 55.9355 80.4363 55.5822 80.401 54.911V51.0253C80.401 50.3188 81.2135 49.9655 81.708 50.4248Z"
                  fill="#F9F9F9"
                />
                <path
                  d="M82.0624 54.4516L82.6982 53.8157C82.6982 53.8157 82.4863 53.5685 82.4156 53.5331C82.0977 53.2152 82.133 52.6147 82.4863 52.2614L84.3232 50.4245C84.6411 50.1066 85.171 50.1066 85.5242 50.4245C85.8421 50.7425 85.8421 51.2723 85.5242 51.6256L85.3123 51.8375L85.2063 51.9435L85.8775 52.6147L85.9834 52.5087L86.1954 52.2968C86.8666 51.6256 86.8666 50.4952 86.1954 49.7887C85.5242 49.0822 84.3938 49.1175 83.6873 49.7887L81.8504 51.6256C81.1792 52.2968 81.1086 53.4978 81.7798 54.169C81.8504 54.275 82.0624 54.4516 82.0624 54.4516Z"
                  fill="#F9F9F9"
                />
                <path
                  d="M86.1934 53.6394L84.0033 51.4492L83.3674 52.0851L85.5576 54.2752C85.8755 54.5931 85.8755 55.123 85.5576 55.4763C85.2397 55.7942 84.7098 55.7942 84.3565 55.4763L84.1446 55.2643L84.0033 55.123L83.3674 55.7589L83.5087 55.9002L83.7207 56.1121C84.3919 56.8186 85.4869 56.8186 86.1934 56.1121C86.8999 55.4056 86.8646 54.3105 86.1934 53.6394Z"
                  fill="#F9F9F9"
                />
                <path
                  d="M97.2853 54.84H96.1549L94.6006 52.7205L93.8234 53.5683V54.84H92.8696V49.8945H93.8234V52.3673L96.0489 49.8945H97.1793L95.2717 51.9787L97.2853 54.84Z"
                  fill="#F9F9F9"
                />
                <path
                  d="M98.981 49.8945H102.619V50.707H99.9347V51.9434H102.337V52.7559H99.9347V53.9922H102.69V54.8047H98.981V49.8945Z"
                  fill="#F9F9F9"
                />
                <path
                  d="M108.625 49.8945L106.823 53.2151V54.84H105.87V53.2504L104.033 49.8945H104.986L106.329 52.226L107.671 49.8945H108.625Z"
                  fill="#F9F9F9"
                />
                <path
                  fill-rule="evenodd"
                  clip-rule="evenodd"
                  d="M114.594 51.0959C114.347 50.7073 114.029 50.3894 113.64 50.1774C113.217 49.9301 112.793 49.8595 112.298 49.8595C111.804 49.8595 111.344 49.9655 110.956 50.1774C110.532 50.3894 110.249 50.7073 110.002 51.0959C109.755 51.4844 109.649 51.9083 109.649 52.3676C109.649 52.8268 109.755 53.2507 110.002 53.6393C110.249 54.0278 110.567 54.3458 110.956 54.5577C111.38 54.805 111.804 54.911 112.298 54.911C112.793 54.911 113.252 54.7697 113.64 54.5577C114.029 54.3458 114.347 54.0278 114.594 53.6393C114.841 53.2507 114.947 52.8268 114.947 52.3676C114.947 51.9083 114.841 51.4844 114.594 51.0959ZM110.849 51.5197C110.991 51.2724 111.203 51.0605 111.45 50.9192C111.732 50.7426 112.015 50.6719 112.298 50.7072C112.58 50.7072 112.863 50.7779 113.11 50.9192C113.357 51.0605 113.569 51.2724 113.711 51.5197C113.852 51.767 113.923 52.0496 113.923 52.3675C113.923 52.6854 113.852 52.968 113.711 53.2153C113.569 53.4626 113.357 53.6745 113.11 53.8158C112.863 53.9571 112.58 54.0278 112.298 54.0278C111.98 54.0278 111.697 53.9571 111.45 53.8158C111.203 53.6745 110.991 53.4626 110.849 53.2153C110.708 52.968 110.637 52.6854 110.637 52.3675C110.637 52.0496 110.708 51.767 110.849 51.5197Z"
                  fill="#F9F9F9"
                />
                <rect
                  x="102.478"
                  y="56.6061"
                  width="3.49717"
                  height="0.812475"
                  fill="#F9F9F9"
                />
                <path
                  fill-rule="evenodd"
                  clip-rule="evenodd"
                  d="M115.727 50.3891L115.868 50.6011H116.01L115.833 50.3538L115.939 50.2478C115.974 50.2125 115.974 50.1772 115.974 50.1065C115.974 50.0359 115.939 49.9652 115.904 49.9299C115.868 49.8946 115.798 49.8593 115.692 49.8593H115.374V50.6011H115.515V50.3891H115.692H115.727ZM115.726 50.2476H115.549V49.965H115.726C115.761 49.965 115.797 49.965 115.832 50.0003C115.867 50.0357 115.867 50.071 115.867 50.1063C115.867 50.1416 115.867 50.177 115.832 50.2123C115.832 50.2476 115.797 50.2476 115.726 50.2476Z"
                  fill="#F9F9F9"
                />
                <circle
                  cx="115.69"
                  cy="50.2119"
                  r="0.7065"
                  stroke="#111111"
                  stroke-width="0.25"
                />
                <circle
                  opacity="0.09"
                  cx="59.1694"
                  cy="94.9113"
                  r="7.28078"
                  fill="#404040"
                />
                <circle
                  opacity="0.09"
                  cx="133.83"
                  cy="94.9113"
                  r="7.28078"
                  fill="#404040"
                />
                <rect
                  opacity="0.09"
                  x="89.4346"
                  y="68.568"
                  width="14.032"
                  height="55.8634"
                  rx="7.01602"
                  fill="#404040"
                />
                <defs>
                  <filter
                    id="filter0_f_6_848"
                    x="0.117432"
                    y="0.118164"
                    width="192.764"
                    height="192.764"
                    filterUnits="userSpaceOnUse"
                    color-interpolation-filters="sRGB"
                  >
                    <feFlood flood-opacity="0" result="BackgroundImageFix" />
                    <feBlend
                      mode="normal"
                      in="SourceGraphic"
                      in2="BackgroundImageFix"
                      result="shape"
                    />
                    <feGaussianBlur
                      stdDeviation="10"
                      result="effect1_foregroundBlur_6_848"
                    />
                  </filter>
                  <linearGradient
                    id="paint0_linear_6_848"
                    x1="96.3612"
                    y1="16.5959"
                    x2="29.7794"
                    y2="177.847"
                    gradientUnits="userSpaceOnUse"
                  >
                    <stop stop-color="#00FA95" />
                    <stop offset="1" stop-color="#00A8F6" />
                  </linearGradient>
                </defs>
              </svg>
            </div>
            <div class="api_icon" id="api_icon">
              <svg class="keyo_api"  viewBox="0 0 268 268" fill="none" xmlns="http://www.w3.org/2000/svg">
<path opacity="0.6" d="M59 49C59 40.7157 65.7157 34 74 34H194C202.284 34 209 40.7157 209 49V169C209 177.284 202.284 184 194 184H74C65.7157 184 59 177.284 59 169V49Z" fill="#F9F9F9"/>
<g filter="url(#filter0_d_6_876)">
<path d="M70.25 58C70.25 50.9584 75.9584 45.25 83 45.25H185C192.042 45.25 197.75 50.9584 197.75 58V160C197.75 167.042 192.042 172.75 185 172.75H83C75.9584 172.75 70.25 167.042 70.25 160V58Z" fill="#F9F9F9"/>
</g>
<path fill-rule="evenodd" clip-rule="evenodd" d="M141.429 126.557C141.429 124.498 143.098 122.829 145.157 122.829H160.535C162.594 122.829 164.263 124.498 164.263 126.557V134.945C164.263 137.004 162.594 138.673 160.535 138.673H145.157C143.098 138.673 141.429 137.004 141.429 134.945V126.557ZM145.157 125.625C144.642 125.625 144.225 126.042 144.225 126.557V134.945C144.225 135.46 144.642 135.877 145.157 135.877H160.535C161.05 135.877 161.467 135.46 161.467 134.945V126.557C161.467 126.042 161.05 125.625 160.535 125.625H145.157Z" fill="black"/>
<path fill-rule="evenodd" clip-rule="evenodd" d="M146.555 119.684C146.555 116.273 149.319 113.509 152.73 113.509C156.14 113.509 158.904 116.273 158.904 119.684V123.761C158.904 124.533 158.278 125.159 157.506 125.159C156.734 125.159 156.108 124.533 156.108 123.761V119.684C156.108 117.818 154.595 116.305 152.73 116.305C150.864 116.305 149.351 117.818 149.351 119.684V123.761C149.351 124.533 148.725 125.159 147.953 125.159C147.181 125.159 146.555 124.533 146.555 123.761V119.684Z" fill="black"/>
<path fill-rule="evenodd" clip-rule="evenodd" d="M112.536 78.0927C113.113 78.0927 113.63 78.4466 113.839 78.984L120.364 95.7602C120.643 96.4798 120.287 97.29 119.567 97.5698C118.848 97.8497 118.037 97.4932 117.758 96.7736L112.536 83.3478L107.315 96.7736C107.036 97.4932 106.225 97.8497 105.506 97.5698C104.786 97.29 104.43 96.4798 104.709 95.7602L111.234 78.984C111.443 78.4466 111.96 78.0927 112.536 78.0927Z" fill="black"/>
<path fill-rule="evenodd" clip-rule="evenodd" d="M116.73 92.0728H108.109V89.2767H116.73V92.0728Z" fill="black"/>
<path fill-rule="evenodd" clip-rule="evenodd" d="M121.624 79.4907C121.624 78.7186 122.249 78.0927 123.022 78.0927H130.711C131.483 78.0927 132.109 78.7186 132.109 79.4907V89.7428C132.109 90.5149 131.483 91.1408 130.711 91.1408H124.42V96.4999C124.42 97.272 123.794 97.8979 123.022 97.8979C122.249 97.8979 121.624 97.272 121.624 96.4999V79.4907ZM124.42 88.3448H129.313V80.8887H124.42V88.3448Z" fill="black"/>
<path fill-rule="evenodd" clip-rule="evenodd" d="M136.769 77.8597C137.541 77.8597 138.167 78.4857 138.167 79.2578V96.733C138.167 97.5051 137.541 98.131 136.769 98.131C135.997 98.131 135.371 97.5051 135.371 96.733V79.2578C135.371 78.4857 135.997 77.8597 136.769 77.8597Z" fill="black"/>
<path d="M150.283 97.1989C150.283 95.3974 151.743 93.9369 153.545 93.9369H159.137C160.939 93.9369 162.399 95.3974 162.399 97.1989V102.791C162.399 104.593 160.939 106.053 159.137 106.053H153.545C151.743 106.053 150.283 104.593 150.283 102.791V97.1989Z" fill="#74D1EA"/>
<path fill-rule="evenodd" clip-rule="evenodd" d="M148.885 97.1989C148.885 94.6252 150.971 92.5388 153.545 92.5388H159.137C161.711 92.5388 163.797 94.6252 163.797 97.1989V102.791C163.797 105.365 161.711 107.451 159.137 107.451H153.545C150.971 107.451 148.885 105.365 148.885 102.791V97.1989ZM153.545 95.3349C152.516 95.3349 151.681 96.1694 151.681 97.1989V102.791C151.681 103.82 152.516 104.655 153.545 104.655H159.137C160.167 104.655 161.001 103.82 161.001 102.791V97.1989C161.001 96.1694 160.167 95.3349 159.137 95.3349H153.545Z" fill="black"/>
<path d="M128.381 110.247C128.381 108.445 129.841 106.985 131.643 106.985H137.235C139.036 106.985 140.497 108.445 140.497 110.247V115.839C140.497 117.641 139.036 119.101 137.235 119.101H131.643C129.841 119.101 128.381 117.641 128.381 115.839V110.247Z" fill="#74D1EA"/>
<path fill-rule="evenodd" clip-rule="evenodd" d="M126.983 110.247C126.983 107.673 129.069 105.587 131.643 105.587H137.235C139.808 105.587 141.895 107.673 141.895 110.247V115.839C141.895 118.413 139.808 120.499 137.235 120.499H131.643C129.069 120.499 126.983 118.413 126.983 115.839V110.247ZM131.643 108.383C130.613 108.383 129.779 109.218 129.779 110.247V115.839C129.779 116.869 130.613 117.703 131.643 117.703H137.235C138.264 117.703 139.099 116.869 139.099 115.839V110.247C139.099 109.218 138.264 108.383 137.235 108.383H131.643Z" fill="black"/>
<path d="M106.012 122.829C106.012 121.028 107.473 119.567 109.274 119.567H114.867C116.668 119.567 118.129 121.028 118.129 122.829V128.421C118.129 130.223 116.668 131.683 114.867 131.683H109.274C107.473 131.683 106.012 130.223 106.012 128.421V122.829Z" fill="#74D1EA"/>
<path fill-rule="evenodd" clip-rule="evenodd" d="M104.614 122.829C104.614 120.255 106.701 118.169 109.274 118.169H114.866C117.44 118.169 119.526 120.255 119.526 122.829V128.421C119.526 130.995 117.44 133.081 114.866 133.081H109.274C106.701 133.081 104.614 130.995 104.614 128.421V122.829ZM109.274 120.965C108.245 120.965 107.41 121.8 107.41 122.829V128.421C107.41 129.451 108.245 130.285 109.274 130.285H114.866C115.896 130.285 116.73 129.451 116.73 128.421V122.829C116.73 121.8 115.896 120.965 114.866 120.965H109.274Z" fill="black"/>
<path fill-rule="evenodd" clip-rule="evenodd" d="M141.196 86.9468C141.196 86.1747 141.822 85.5488 142.594 85.5488H156.108C156.88 85.5488 157.506 86.1747 157.506 86.9468V93.9369C157.506 94.709 156.88 95.3349 156.108 95.3349C155.336 95.3349 154.71 94.709 154.71 93.9369V88.3449H142.594C141.822 88.3449 141.196 87.7189 141.196 86.9468Z" fill="black"/>
<path fill-rule="evenodd" clip-rule="evenodd" d="M118.362 100.461L118.362 109.548C118.362 109.919 118.214 110.274 117.952 110.537C117.69 110.799 117.334 110.946 116.964 110.946L113.469 110.946L113.469 118.402C113.469 119.174 112.843 119.8 112.07 119.8C111.298 119.8 110.672 119.174 110.672 118.402L110.672 109.548C110.672 108.776 111.298 108.15 112.07 108.15L115.566 108.15L115.566 100.461C115.566 99.6888 116.191 99.0629 116.964 99.0629C117.736 99.0629 118.362 99.6888 118.362 100.461Z" fill="black"/>
<path fill-rule="evenodd" clip-rule="evenodd" d="M135.604 102.791L135.604 106.752C135.604 107.524 134.978 108.15 134.206 108.15C133.434 108.15 132.808 107.524 132.808 106.752L132.808 104.189L128.847 104.189C128.476 104.189 128.12 104.042 127.858 103.78C127.596 103.517 127.449 103.162 127.449 102.791L127.449 100.228C127.449 99.4559 128.075 98.83 128.847 98.83C129.619 98.83 130.245 99.4559 130.245 100.228L130.245 101.393L134.206 101.393C134.978 101.393 135.604 102.019 135.604 102.791Z" fill="black"/>
<defs>
<filter id="filter0_d_6_876" x="0.25" y="0.25" width="267.5" height="267.5" filterUnits="userSpaceOnUse" color-interpolation-filters="sRGB">
<feFlood flood-opacity="0" result="BackgroundImageFix"/>
<feColorMatrix in="SourceAlpha" type="matrix" values="0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 127 0" result="hardAlpha"/>
<feOffset dy="25"/>
<feGaussianBlur stdDeviation="35"/>
<feColorMatrix type="matrix" values="0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0.1 0"/>
<feBlend mode="normal" in2="BackgroundImageFix" result="effect1_dropShadow_6_876"/>
<feBlend mode="normal" in="SourceGraphic" in2="effect1_dropShadow_6_876" result="shape"/>
</filter>
</defs>
</svg>

            </div>
          </div>
          <div class="output_right" id="output_right">
            <ServerItem :Animation="Animation" :ListValue="ListValue" />
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
import ServerItem from "./ServerItem.vue";
import axios from "axios";
export default {
  name: "Home",
  components: {
    ServerItem,
  },
  data() {
    return {
      ListValue: 0,
      Animation: "",
      notification: {
        title: "",
        message: "",
        type: "",
      },
      disabled: true,
      numUser: "",
      numMatch: "",
      NumMatchRate: "",
      InitialData: {
        summary: {
          run_time: "-",
          throughput_avg: "-",
          latency_min: "-",
          latency_avg: "-",
          latency_max: "-",
        },
      },
      TestData: {
        summary: {
          run_time: "-",
          throughput_avg: "-",
          latency_min: "-",
          latency_avg: "-",
          latency_max: "-",
        },
      },
    };
  },
  computed: {
    numUsers: {
      get: function () {
        if (isNaN(this.numUser)) {
          this.numUser = 0;
        }
        return this.numberWithCommas(this.numUser);
      },
      set: function (newValue) {
        const formattedValue = newValue.toString().replace(/\D/g, "");
        const inputfield = document.getElementById("numberUsers");
        inputfield.value = this.numberWithCommas(formattedValue);
        if (!isNaN(parseInt(formattedValue))) {
          this.numUser = parseInt(formattedValue);
        }
      },
    },
    numMatches: {
      get: function () {
        if (isNaN(this.numMatch)) {
          this.numMatch = 0;
        }
        return this.numberWithCommas(this.numMatch);
      },
      set: function (newValue) {
        const formattedValue = newValue.toString().replace(/\D/g, "");
        const inputfield = document.getElementById("numberMatches");
        inputfield.value = this.numberWithCommas(formattedValue);
        if (!isNaN(parseInt(formattedValue))) {
          this.numMatch = parseInt(formattedValue);
        }
      },
    },
  },
  methods: {
    showCustomeNotification(title, msg, type) {
      const notiId = document.getElementById("notification");
      this.$data.notification.title = title;
      this.$data.notification.message = msg;
      this.$data.notification.type = type;
      notiId.style.display = "block";
      setTimeout(() => {
        notiId.style.display = "none";
      }, 4000);
    },

    numberWithCommas(amount) {
      return amount.toString().replace(/\B(?=(\d{3})+(?!\d))/g, ",");
    },
    parsednumber(newAmount) {
      return parseInt(newAmount.replace(/,/g, ""));
    },
    animateList() {
      setTimeout(() => {
        const output = document.getElementById("output_right");
        const outputChilds = output.children;
        for (let i = 0; i < outputChilds.length; i++) {
          setTimeout(() => {
            outputChilds[i].style.opacity = 1;
          }, 700 * i);
        }
      }, 500);
    },
    resetAnimateList() {
      const output = document.getElementById("output_right");
      const outputChilds = output.children;
      for (let i = 0; i < outputChilds.length; i++) {
        outputChilds[i].style.opacity = 0;
      }
    },
    numMat(e) {
      e.preventDefault();
      this.$data.InitialData = this.$data.TestData;
      this.resetAnimateList();
      const InputValue = this.$data.numUser;
      if (InputValue <= 0 || InputValue > 100000001) {
        this.showCustomeNotification(
          "Error",
          "Please enter a number between 1 and 100,000,000",
          "error"
        );
        return;
      } else {
        const value = 8000000;
        const divide = InputValue / value;
        if (InputValue < value) {
          const result = 1;
          this.$data.ListValue = result;
        } else {
          const result = Math.ceil(divide);
          this.$data.ListValue = result;
        }
        this.$data.Animation = "";
        this.animateList();
        const button = document.getElementById("keyo_start");
        const servers = document.getElementById("matchServer");

        button.removeAttribute("disabled");
        button.classList.remove("disabled");
        servers.classList.add("showServer");
      }
    },
    onSubmit(e) {
      e.preventDefault();
      const api_icon = document.getElementById("api_icon");
      if (this.$data.numMatch <= 0 || this.$data.numMatch > 100001) {
        this.showCustomeNotification(
          "Error",
          "Please enter a number between 1 and 100,000",
          "error"
        );
        return;
      } else if (this.$data.numUser <= 0 || this.$data.numUser > 100000001) {
        this.showCustomeNotification(
          "Error",
          "Please enter a number between 1 and 100,000,000",
          "error"
        );
        return;
      } else {
        this.$data.InitialData = this.$data.TestData;
        this.$data.Animation = "breathing";
        api_icon.classList.add("apibreath");
        axios(
          "https://protected-atoll-67310.herokuapp.com/api/match-request/",
          {
            method: "post",
            data: {
              numUsers: this.$data.numUser,
              numMatches: this.$data.numMatch,
              NumMatchRate: this.$data.NumMatchRate,
            },
          }
        )
          .then((response) => {
            this.$data.InitialData = response.data.response;
            this.$data.Animation = "";
            api_icon.classList.remove("apibreath");
          })
          .catch((error) => {
            console.log(error);
          });
      }
    },
    deleteUsers(e) {
      e.preventDefault();
      this.$data.numUser = "";
      this.$data.numMatch = "";
      this.$data.NumMatchRate = "";
      this.$data.InitialData = {
        summary: {
          run_time: "-",
          throughput_avg: "-",
          latency_min: "-",
          latency_avg: "-",
          latency_max: "-",
        },
      };
      this.$data.TestData = {
        summary: {
          run_time: "-",
          throughput_avg: "-",
          latency_min: "-",
          latency_avg: "-",
          latency_max: "-",
        },
      };
      this.$data.ListValue = 0;
      this.$data.Animation = "";
      this.resetAnimateList();
      const button = document.getElementById("keyo_start");
      const servers = document.getElementById("matchServer");
      button.setAttribute("disabled", "disabled");
      button.classList.add("disabled");
      servers.classList.remove("showServer");
    },
  },
};
</script>

<style>
.logo {
  transform: translate(-17px, 10px);
}
.matchServer {
  opacity: 0;
  transition: 0.5s ease-in-out;
}
.showServer {
  opacity: 1;
}
.keyo_logo {
  width: 80px;
  height: auto;
}

.keyo_main {
  max-width: 1150px;
  margin: 0 auto;
  padding-bottom: 2rem;
}

.keyo_row {
  display: flex;
  margin: 0 -15px;
  flex-direction: row;
  justify-content: space-between;
}

.keyo_card {
  width: 100%;
  max-width: 345px;
  padding: 25px 15px;
  margin-bottom: 30px;
  background-color: #fff;
  border-radius: 5px;
  box-shadow: rgba(0, 0, 0, 0.05) 0px 6px 24px 0px,
    rgba(0, 0, 0, 0.08) 0px 0px 0px 1px;
}

.heading {
  font-weight: 700;
  margin-bottom: 15px;
  font-style: normal;
  font-weight: 700;
  font-size: 25px;
  line-height: 30px;
}

.keyo_card p {
  margin-bottom: 0;
  color: #666;
  margin-bottom: 1rem;
  font-style: normal;
  font-weight: 400;
  font-size: 10px;
  line-height: 16px;
}

.keyo_input {
  width: 90%;
  padding: 5px 10px;
  margin-bottom: 1rem;
  background-color: rgb(245, 245, 245);
  border-radius: 3px;
  border: none;
}

.keyo_button {
  font-size: 0.7rem;
  padding: 5px 15px;
  background-color: #000000;
  color: #fff;
  border: none;
  border-radius: 5px;
  font-weight: 500;
  cursor: pointer;
  transition: 0.4s;
}

.keyo_button:hover {
  background-color: transparent;
  box-shadow: inset 0 0 0 1px #000000;
  color: #000000;
}

.keyo_label {
  font-style: normal;
  font-weight: 500;
  font-size: 10px;
  line-height: 12px;
  margin-bottom: 0.5rem;
}




table tr td span {
  font-style: normal;
  font-weight: 400;
  font-size: 8px;
  line-height: 10px;
  font-variant: small-caps;
  color: #828282;
}

table tr td {
  padding: 0.5rem 2rem 0.5rem 0.5rem;
  font-style: normal;
  font-weight: 400;
  font-size: 10px;
  line-height: 15px;
}

table tr td:first-child {
  font-weight: 500;
}

table {
  border-spacing: 0;
  width: 100%;
  border: 1px solid #ddd;
  border-radius: 5px;
}

table tr{
  border-bottom: 1px solid #ddd;
}

table tr:last-child {
  border-bottom: none;
}

table tr:hover {
  background-color: rgb(242, 242, 242);
  cursor: pointer;
}

.keyo_td{
  padding: 0.5rem 0.6rem 0.5rem 0.5rem;
}

.throughput {
  width: 97%;
  font-family: 'Montserrat', sans-serif;
  font-style: normal;
  font-weight: 400;
  font-size: 12px;
  line-height: 28px;
  padding: 10px;
}
.output_card {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  padding: 80px 100px 40px;
  margin-bottom: 30px;
}

input{
  font-family: 'Montserrat', sans-serif;
  font-style: normal;
  font-weight: 400;
  font-size: 12px;
  line-height: 28px;
}

button{
  font-family: 'Montserrat', sans-serif;
  font-style: normal;
  font-weight: 500;
  font-size: 13px;
  line-height: 28px;
}


/* ============= Animations =============== */

@-webkit-keyframes breathing {
  0% {
    -moz-box-shadow: 0px 1px -1px #7AE1BF;
    -webkit-box-shadow: 0px 1px -1px #7AE1BF;
    box-shadow: 0px 1px -1px #7AE1BF;
  }
  

  50% {
    -moz-box-shadow: 0px 0px 0px 4px #7AE1BF;
    -webkit-box-shadow: 0px 0px 0px 4px #7AE1BF;
    box-shadow: 0px 0px 0px 4px #7AE1BF;
  }
}

@-moz-keyframes breathing {
  0% {
    -moz-box-shadow: 0px 1px 1px #7AE1BF;
    -webkit-box-shadow: 0px 1px 1px #7AE1BF;
    box-shadow: 0px 1px 1px #7AE1BF;
  }

  50% {
    -moz-box-shadow: 0px 0px 0px 4px #7AE1BF;
    -webkit-box-shadow: 0px 0px 0px 4px #7AE1BF;
    box-shadow: 0px 0px 0px 4px #7AE1BF;
  }
}

@keyframes breathing {
  0% {
    -moz-box-shadow: 0px 1px 1px #7AE1BF;
    -webkit-box-shadow: 0px 1px 1px #7AE1BF;
    box-shadow: 0px 1px 1px #7AE1BF;
  }

  50% {
    -moz-box-shadow: 0px 0px 0px 4px #7AE1BF;
    -webkit-box-shadow: 0px 0px 0px 4px #7AE1BF;
    box-shadow: 0px 0px 0px 4px #7AE1BF;
  }
}

@-webkit-keyframes apibreath {
  0% {
    -moz-box-shadow: 0px 1px -1px #74D1EA;
    -webkit-box-shadow: 0px 1px -1px #74D1EA;
    box-shadow: 0px 1px -1px #74D1EA;
  }
  

  50% {
    -moz-box-shadow: 0px 0px 0px 4px #74D1EA;
    -webkit-box-shadow: 0px 0px 0px 4px #74D1EA;
    box-shadow: 0px 0px 0px 4px #74D1EA;
  }
}

@-moz-keyframes apibreath {
  0% {
    -moz-box-shadow: 0px 1px 1px #74D1EA;
    -webkit-box-shadow: 0px 1px 1px #74D1EA;
    box-shadow: 0px 1px 1px #74D1EA;
  }

  50% {
    -moz-box-shadow: 0px 0px 0px 4px #74D1EA;
    -webkit-box-shadow: 0px 0px 0px 4px #74D1EA;
    box-shadow: 0px 0px 0px 4px #74D1EA;
  }
}

@keyframes apibreath {
  0% {
    -moz-box-shadow: 0px 1px 1px #74D1EA;
    -webkit-box-shadow: 0px 1px 1px #74D1EA;
    box-shadow: 0px 1px 1px #74D1EA;
  }

  50% {
    -moz-box-shadow: 0px 0px 0px 4px #74D1EA;
    -webkit-box-shadow: 0px 0px 0px 4px #74D1EA;
    box-shadow: 0px 0px 0px 4px #74D1EA;
  }
}

.breathing {
  -webkit-animation: breathing 1s infinite;
  -moz-animation: breathing 1s infinite;
  animation: breathing 1s infinite;
}

.breath {
  -webkit-animation: breath 1s infinite;
  -moz-animation: breath 1s infinite;
  animation: breath 1s infinite;
}

.apibreath {
  -webkit-animation: apibreath 1s infinite;
  -moz-animation: apibreath 1s infinite;
  animation: apibreath 1s infinite;
}

.keyo_output {
  margin-bottom: 2rem;
  width: 103%;
  transform: translateX(-1.4%);
  height: 420px;
  background-color: #fff;
  border-radius: 5px;
  box-shadow: rgba(0, 0, 0, 0.05) 0px 6px 24px 0px,
    rgba(0, 0, 0, 0.08) 0px 0px 0px 1px;
}

.main_icon {
  display: block;
  margin-bottom: 6rem;
  border-radius: 50%;
  width: 90px;
  height: 90px;
  transform: translateY(10px);
}

.keyo_wave {
  width: 110px;
  border-radius: 50%;
  transform: translate(-10px , -10px);
}

.output_left {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  transform: translate(-70px,76px);
}

.main_icon::after {
  content: url("../assets/serverArrow.svg");
  display: block;
  transform: translate(116px, -80px);
  transition: all 0.5s ease-in-out;
}

.server_icon {
  width: 40px;
  height: 37px;
  margin-right: 25px;
  padding: 7px;
  border-radius: 5px;
}

.servers_icon{
  width: 133px;
  transform: translate(-46px, -34px);
}

.disabled {
  opacity: 0.5;
  pointer-events: none;
}
/* get odd value in server_icon */

.output_right {
  width: 395px;
  transform: translate(50px,105px);
  position: relative;
}

.server {
  z-index: 1;
  opacity: 0;
  transition: all 0.6s ease-in-out;
}

/* 
.server:nth-child(2)::before {
  content: url("../assets/Arrow.svg");
  position: absolute;
  transform: translate(-44px, -48px);
  transition: all 0.5s ease-in-out;
  z-index: -1;
}

.server:nth-child(3)::before {
  content: url("../assets/Arrow.svg");
  position: absolute;
  transform: translate(-44px, -48px);
  transition: all 0.5s ease-in-out;
  z-index: -1;
}

.server:nth-child(4)::before {
  content: url("../assets/Arrow.svg");
  position: absolute;
  transform: translate(-44px, -48px);
  transition: all 0.5s ease-in-out;
  z-index: -1;
}*/

.server:nth-child(6)::before {
  content: url("../assets/curvedArrow1.svg");
  position: absolute;
  transform: translate(-185px, 17px);
  transition: all 0.5s ease-in-out;
  z-index: -1;
} 

.server:nth-child(11)::before {
  content: url("../assets/curvedArrow2.svg");
  position: absolute;
  transform: translate(-185px, -126px);
  transition: all 0.5s ease-in-out;
  z-index: -1;
} 

.server:nth-child(1)::before {
  position: absolute;
  transition: all 0.5s ease-in-out;
  z-index: -1;
  content: url("../assets/straightArrow.svg") !important;
  transform: translate(-250px, 14px);
}

.server:nth-child(1){
  transform: translate(0px, 0px);
}

.server:nth-child(2){
  transform: translate(115px, -50px);
}

.server:nth-child(3){
  transform: translate(230px, -100px);
}

.server:nth-child(4){
  transform: translate(345px, -150px);
}

.server:nth-child(5){
  transform: translate(460px, -200px);
}

.server:nth-child(6){
  transform: translate(0px, -404px);
}

.server:nth-child(7){
  transform: translate(115px, -454px);
}

.server:nth-child(8){
  transform: translate(230px, -504px);
}

.server:nth-child(9){
  transform: translate(345px, -554px);
}

.server:nth-child(10){
  transform: translate(460px, -604px);
}

.server:nth-child(11){
  transform: translate(0px, -359px);
}

.server:nth-child(12){
  transform: translate(115px, -409px);
}

.server:nth-child(13){
  transform: translate(230px, -459px);
}


.server:nth-child(14){
  transform: translate(345px, -509px);
}

.server:nth-child(15){
  transform: translate(460px, -559px);
}


.server:nth-child(2)::before,
.server:nth-child(3)::before,
.server:nth-child(4)::before,
.server:nth-child(5)::before,
.server:nth-child(7)::before,
.server:nth-child(8)::before,
.server:nth-child(9)::before,
.server:nth-child(10)::before,
.server:nth-child(12)::before,
.server:nth-child(13)::before,
.server:nth-child(14)::before,
.server:nth-child(15)::before {
  content: url("../assets/Arrow.svg");
  position: absolute;
  transform: translate(-52px, 12px);
  transition: all 0.5s ease-in-out;
  z-index: -1;
}



/* .server:nth-child(6),
.server:nth-child(7),
.server:nth-child(8),
.server:nth-child(9),
.server:nth-child(10) {
  transform: translateY(-404px);
} */

/* .server:nth-child(11),
.server:nth-child(12),
.server:nth-child(13),
.server:nth-child(14),
.server:nth-child(15) {
  transform: translateY(-6px);
} */



.api_icon {
  transform: translate(15px, 19px);
  z-index: 2;
  width: 74px;
  height: 72px;
  border-radius: 10px;
}

.keyo_api {
  width: 150px;
  transform: translate(-38px, -25px);
}

.main_noti {
  position: absolute;
  right: 10px;
  display: none;
}

.notification {
  position: relative;
  display: inline-block;
  max-width: 300px;
  padding: 10px 15px;
  border-radius: 4px;
  background-color: #141619;
  color: #f6f5f9;
  box-shadow: 0 1px 10px rgba(0, 0, 0, 0.1);
  transform: translateY(30px);
  opacity: 0;
  visibility: hidden;
  animation: fade 4s linear forwards;
  cursor: pointer;
}

.progress {
  position: absolute;
  left: 5px;
  bottom: 5px;
  width: 0;
  height: 3px;
  background-image: linear-gradient(to right, #529bdb, #3250bf);
  border-radius: 4px;
  animation: progress 3s 0.25s linear forwards;
}

@keyframes fade {
  5% {
    opacity: 1;
    visibility: visible;
    transform: translateY(0px);
  }
  90% {
    opacity: 1;
    transform: translateY(0px);
  }
  95% {
    opacity: 0;
  }
  100% {
    opacity: 0;
    transform: translateY(-30px);
    visibility: hidden;
  }
}

@keyframes progress {
  to {
    width: calc(100% - 10px);
  }
}

.notification:hover {
  animation-play-state: paused;
}

.notification P {
  font-size: 12px;
}
.notification:hover .progress {
  animation-play-state: paused;
}
.error {
  background-color: #ff2525;
}
.success {
  background-color: #00ed9b;
  color: #000000;
}
.reset_button{
  background-color: #F2F2F2;
  color: #000;
}

</style>
