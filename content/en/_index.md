---
title: Kube-VIM
linkTitle: Kube-VIM
---

<section class="kv-hero">
  <div class="container">
    <div class="row align-items-center g-5">
      <div class="col-lg-6 kv-hero__text">
        <h1 class="kv-hero__title">Kube-VIM</h1>
        <p class="kv-hero__tagline">NFV, the Kubernetes way</p>
        <p class="kv-hero__sub">
          An ETSI NFV-MANO compliant Virtual Infrastructure Manager that runs
          virtual network functions on Kubernetes, next to your cloud-native
          workloads.
        </p>
        <div class="kv-hero__cta">
          <a class="btn btn-lg btn-light fw-semibold" href="/docs/getting-started/">
            Get started <i class="fas fa-arrow-right ms-2"></i>
          </a>
          <a class="btn btn-lg btn-outline-light" href="https://github.com/kube-nfv/kube-vim">
            <i class="fab fa-github me-2"></i> GitHub
          </a>
        </div>
        <p class="kv-hero__note">Open source · Apache 2.0 · backed by Retelith</p>
      </div>
      <div class="col-lg-6 kv-hero__art" aria-hidden="true">
        <svg class="kv-mesh" viewBox="0 0 640 480" xmlns="http://www.w3.org/2000/svg">
          <defs>
            <radialGradient id="kvGlow" cx="70%" cy="42%" r="58%">
              <stop offset="0%" stop-color="#ffffff" stop-opacity="0.30"/>
              <stop offset="55%" stop-color="#a5f3fc" stop-opacity="0.10"/>
              <stop offset="100%" stop-color="#ffffff" stop-opacity="0"/>
            </radialGradient>
            <linearGradient id="kvEdge" gradientUnits="userSpaceOnUse" x1="0" y1="0" x2="640" y2="0">
              <stop offset="0" stop-color="#ffffff" stop-opacity="0"/>
              <stop offset="0.4" stop-color="#c7d2fe" stop-opacity="0.28"/>
              <stop offset="1" stop-color="#67e8f9" stop-opacity="0.9"/>
            </linearGradient>
            <linearGradient id="kvNode" gradientUnits="userSpaceOnUse" x1="0" y1="0" x2="640" y2="0">
              <stop offset="0" stop-color="#c7d2fe" stop-opacity="0.18"/>
              <stop offset="0.5" stop-color="#e0e7ff" stop-opacity="0.7"/>
              <stop offset="1" stop-color="#a5f3fc" stop-opacity="1"/>
            </linearGradient>
            <radialGradient id="kvHubHalo" cx="50%" cy="50%" r="50%">
              <stop offset="0%" stop-color="#1e1b4b" stop-opacity="0.55"/>
              <stop offset="55%" stop-color="#1e1b4b" stop-opacity="0.28"/>
              <stop offset="100%" stop-color="#1e1b4b" stop-opacity="0"/>
            </radialGradient>
            <filter id="kvGlowF" x="-60%" y="-60%" width="220%" height="220%">
              <feGaussianBlur stdDeviation="2.6" result="b"/>
              <feMerge><feMergeNode in="b"/><feMergeNode in="SourceGraphic"/></feMerge>
            </filter>
          </defs>
          <circle cx="470" cy="230" r="180" fill="url(#kvGlow)"/>
          <g stroke="url(#kvEdge)" stroke-width="1.25" fill="none">
            <line x1="45" y1="140" x2="150" y2="210"/>
            <line x1="120" y1="90" x2="230" y2="110"/>
            <line x1="70" y1="300" x2="150" y2="210"/>
            <line x1="150" y1="210" x2="250" y2="280"/>
            <line x1="150" y1="210" x2="230" y2="110"/>
            <line x1="230" y1="110" x2="330" y2="190"/>
            <line x1="250" y1="280" x2="330" y2="190"/>
            <line x1="250" y1="280" x2="300" y2="400"/>
            <line x1="330" y1="190" x2="400" y2="120"/>
            <line x1="210" y1="360" x2="300" y2="400"/>
            <line x1="250" y1="280" x2="210" y2="360"/>
            <line x1="330" y1="190" x2="430" y2="260"/>
            <line x1="250" y1="280" x2="430" y2="260"/>
            <line x1="400" y1="120" x2="490" y2="180"/>
            <line x1="400" y1="120" x2="535" y2="80"/>
            <line x1="490" y1="180" x2="470" y2="230"/>
            <line x1="430" y1="260" x2="470" y2="230"/>
            <line x1="455" y1="380" x2="520" y2="310"/>
            <line x1="520" y1="310" x2="470" y2="230"/>
            <line x1="490" y1="180" x2="560" y2="230"/>
            <line x1="560" y1="230" x2="470" y2="230"/>
            <line x1="535" y1="80" x2="600" y2="140"/>
            <line x1="600" y1="140" x2="490" y2="180"/>
            <line x1="560" y1="230" x2="600" y2="140"/>
            <line x1="560" y1="230" x2="610" y2="290"/>
            <line x1="610" y1="290" x2="520" y2="310"/>
            <line x1="590" y1="370" x2="520" y2="310"/>
            <line x1="590" y1="370" x2="575" y2="440"/>
            <line x1="455" y1="380" x2="575" y2="440"/>
            <line x1="470" y1="230" x2="400" y2="120"/>
            <line x1="470" y1="230" x2="560" y2="230"/>
            <line x1="470" y1="230" x2="455" y2="380"/>
          </g>
          <g fill="url(#kvNode)">
            <circle cx="45" cy="140" r="4"/>
            <circle cx="120" cy="90" r="4"/>
            <circle cx="70" cy="300" r="4"/>
            <circle cx="150" cy="210" r="5"/>
            <circle cx="230" cy="110" r="5"/>
            <circle cx="250" cy="280" r="6"/>
            <circle cx="300" cy="400" r="5"/>
            <circle cx="330" cy="190" r="6"/>
            <circle cx="210" cy="360" r="4"/>
            <circle cx="400" cy="120" r="6"/>
            <circle cx="430" cy="260" r="7" class="pulse"/>
            <circle cx="455" cy="380" r="6"/>
            <circle cx="490" cy="180" r="6" class="pulse"/>
            <circle cx="520" cy="310" r="7" class="pulse"/>
            <circle cx="535" cy="80" r="6"/>
            <circle cx="560" cy="230" r="7" class="pulse"/>
            <circle cx="590" cy="370" r="6"/>
            <circle cx="600" cy="140" r="6"/>
            <circle cx="610" cy="290" r="7"/>
            <circle cx="575" cy="440" r="5"/>
          </g>
          <g fill="#7dd3fc" filter="url(#kvGlowF)">
            <circle r="3"><animateMotion dur="4s" repeatCount="indefinite" path="M45,140 L150,210 L250,280 L430,260 L470,230"/></circle>
            <circle r="2.6"><animateMotion dur="5s" begin="1s" repeatCount="indefinite" path="M120,90 L230,110 L330,190 L400,120 L490,180 L470,230"/></circle>
            <circle r="3"><animateMotion dur="4.5s" begin="0.6s" repeatCount="indefinite" path="M470,230 L560,230 L600,140"/></circle>
            <circle r="2.6"><animateMotion dur="5.5s" begin="2s" repeatCount="indefinite" path="M470,230 L520,310 L590,370"/></circle>
            <circle r="2.4"><animateMotion dur="6s" begin="1.4s" repeatCount="indefinite" path="M70,300 L150,210 L250,280 L430,260 L470,230"/></circle>
          </g>
          <circle cx="470" cy="230" r="110" fill="url(#kvHubHalo)"/>
          <g transform="translate(409,169) scale(1.9)">
            <circle cx="32" cy="32" r="22" fill="none" stroke="#c7d2fe" stroke-width="5" stroke-dasharray="20 18" stroke-dashoffset="10" stroke-linecap="round"/>
            <circle cx="32" cy="10" r="7" fill="#e0e7ff"/>
            <circle cx="51" cy="43" r="7" fill="#e0e7ff"/>
            <circle cx="13" cy="43" r="7" fill="#e0e7ff"/>
            <rect x="23" y="23" width="18" height="18" rx="4" fill="#22d3ee"/>
          </g>
          <circle cx="470" cy="230" r="78" fill="none" stroke="#67e8f9" stroke-opacity="0.25" stroke-width="1" class="pulse pulse--slow"/>
        </svg>
      </div>
    </div>
  </div>
</section>

<section class="kv-section kv-section--flow" id="how-it-fits">
  <div class="container">
    <div class="kv-section-head">
      <span class="kv-eyebrow">How it fits</span>
      <h2>From ETSI request to running VNF</h2>
      <p>Your orchestrator speaks the standard reference points. Kube-VIM turns what it asks for into Kubernetes objects.</p>
    </div>
    <div class="kv-flow" role="img" aria-label="Any ETSI NFV-MANO compatible orchestrator drives Kube-VIM over the Or-Vi, Vi-Vnfm and SOL 013 reference points. Kube-VIM creates and reconciles Kubernetes resources through KubeVirt, CDI, Kube-OVN and Multus, which run the VNF virtual machines. The VNFs share one cluster with the CNF workloads that are already running there, on the same nodes, network fabric and tooling, on any Kubernetes distribution at the edge or in the cloud.">
      <div class="kv-flow__node">
        <span class="kv-flow__glyph kv-flow__glyph--mano" aria-hidden="true">
          <i class="fas fa-sitemap"></i>
        </span>
        <div>
          <h3>NFVO / VNFM</h3>
          <p>Any ETSI NFV-MANO compatible orchestrator drives Kube-VIM over the standard reference points.</p>
        </div>
      </div>
      <div class="kv-flow__conn">
        <span class="kv-flow__stem"></span>
        <span class="kv-flow__pill">Or-Vi &middot; Vi-Vnfm &middot; SOL 013</span>
        <span class="kv-flow__stem"></span>
        <span class="kv-flow__cap"></span>
      </div>
      <div class="kv-flow__vim">
        <div class="kv-flow__vim-text">
          <h3>Kube-VIM</h3>
          <p>Translates ETSI MANO requests into Kubernetes resources. Stateless, with no external database.</p>
        </div>
        <div class="kv-flow__chips">
          <span class="kv-flow__chip">gRPC</span>
          <span class="kv-flow__chip">REST / OpenAPI</span>
        </div>
      </div>
      <div class="kv-flow__conn">
        <span class="kv-flow__stem"></span>
        <span class="kv-flow__note">creates and reconciles</span>
        <span class="kv-flow__stem"></span>
        <span class="kv-flow__cap"></span>
      </div>
      <div class="kv-flow__krm">
        <span class="kv-flow__eyebrow">Kubernetes resource model</span>
        <div class="kv-flow__comps">
          <div class="kv-flow__comp"><b>KubeVirt</b><span>VM compute</span></div>
          <div class="kv-flow__comp"><b>CDI</b><span>Disk images</span></div>
          <div class="kv-flow__comp"><b>Kube-OVN</b><span>Networks and subnets</span></div>
          <div class="kv-flow__comp"><b>Multus</b><span>Multi-NIC, SR-IOV</span></div>
        </div>
      </div>
      <div class="kv-flow__conn kv-flow__conn--split">
        <span>
          <span class="kv-flow__stem"></span>
          <span class="kv-flow__cap"></span>
        </span>
        <span></span>
      </div>
      <div class="kv-flow__cluster">
        <div class="kv-flow__cluster-head">
          <span class="kv-flow__eyebrow">One cluster</span>
          <span>Kube-VIM creates the VNFs. Your containers are already here.</span>
          <span class="kv-flow__where"><i class="fas fa-location-dot" aria-hidden="true"></i> Edge or cloud</span>
        </div>
        <div class="kv-flow__loads">
          <div class="kv-flow__load kv-flow__load--vnf">
            <span class="kv-flow__glyph kv-flow__glyph--vnf" aria-hidden="true">
              <i class="fas fa-display"></i>
            </span>
            <div>
              <h3>VNF virtual machines</h3>
              <p>KubeVirt workloads</p>
              <span class="kv-flow__tag kv-flow__tag--managed">Created by Kube-VIM</span>
            </div>
          </div>
          <div class="kv-flow__load">
            <span class="kv-flow__glyph kv-flow__glyph--cnf" aria-hidden="true">
              <i class="fas fa-cubes"></i>
            </span>
            <div>
              <h3>CNF workloads</h3>
              <p>Your existing containers</p>
              <span class="kv-flow__tag kv-flow__tag--peer">Runs alongside</span>
            </div>
          </div>
        </div>
        <div class="kv-flow__fabric">
          <span><b>Same nodes</b> and resource pool</span>
          <span><b>Same network fabric</b> via Multus and SR-IOV</span>
          <span><b>Same tooling</b> and cluster APIs</span>
        <span><b>Any distribution</b>, from an edge box to a datacentre</span>
        </div>
      </div>
    </div>
  </div>
</section>

<section class="kv-section kv-section--tint">
  <div class="container">
    <div class="kv-section-head">
      <span class="kv-eyebrow">Why Kube-VIM</span>
      <h2>Carrier NFV, without a parallel stack</h2>
      <p>Standards-compliant on the outside, plain Kubernetes on the inside.</p>
    </div>
    <div class="row g-4">
      <div class="col-md-6 col-lg-3">
        <div class="kv-card">
          <div class="kv-card__icon"><i class="fas fa-cubes"></i></div>
          <h3>KRM-native</h3>
          <p>Every managed resource is a Kubernetes object in etcd. Kube-VIM reconciles NFV resources like a native controller, with no external database and no drift.</p>
        </div>
      </div>
      <div class="col-md-6 col-lg-3">
        <div class="kv-card">
          <div class="kv-card__icon"><i class="fas fa-plug"></i></div>
          <h3>ETSI VIM, any NFVO</h3>
          <p>Or-Vi and Vi-Vnfm over gRPC and REST, with a generated OpenAPI client. Validated with OSM through an OSM connector.</p>
        </div>
      </div>
      <div class="col-md-6 col-lg-3">
        <div class="kv-card">
          <div class="kv-card__icon"><i class="fas fa-bolt"></i></div>
          <h3>Line-rate data plane</h3>
          <p>SR-IOV with hardware offload for near-line-rate throughput. Overlay, underlay, and SR-IOV networks today; vDPA and vhost-user planned.</p>
        </div>
      </div>
      <div class="col-md-6 col-lg-3">
        <div class="kv-card">
          <div class="kv-card__icon"><i class="fas fa-layer-group"></i></div>
          <h3>Converged NFV</h3>
          <p>Run VNFs alongside your CNFs on the same hardware and the same network fabric. Convergence comes from being Kubernetes-native.</p>
        </div>
      </div>
      <div class="col-md-6 col-lg-3">
        <div class="kv-card">
          <div class="kv-card__icon"><i class="fas fa-server"></i></div>
          <h3>Hyperconverged and portable</h3>
          <p>Runs on any Kubernetes distribution. Proven on Talos Linux in a hyperconverged edge topology.</p>
        </div>
      </div>
      <div class="col-md-6 col-lg-3">
        <div class="kv-card">
          <div class="kv-card__icon"><i class="fas fa-rocket"></i></div>
          <h3>Easy to deploy</h3>
          <p>A single Helm bundle ships Kube-VIM together with the components it drives. GitOps-friendly and simple to stand up.</p>
        </div>
      </div>
      <div class="col-md-6 col-lg-3">
        <div class="kv-card">
          <div class="kv-card__icon"><i class="fas fa-cube"></i></div>
          <h3>Built on trusted OSS</h3>
          <p>Stands on KubeVirt, CDI, Kube-OVN, and Multus, with no vendor, NIC, or distribution lock-in.</p>
        </div>
      </div>
      <div class="col-md-6 col-lg-3">
        <div class="kv-card">
          <div class="kv-card__icon"><i class="fas fa-chart-line"></i></div>
          <h3>Observable</h3>
          <p>Prometheus metrics out of the box, with correlation labels that tie backend series to ETSI resource IDs.</p>
        </div>
      </div>
    </div>
  </div>
</section>

<section class="kv-section">
  <div class="container">
    <div class="kv-section-head">
      <span class="kv-eyebrow">What is Kube-VIM</span>
      <h2>A thin control plane for NFV on Kubernetes</h2>
      <p>It sits between your NFV orchestrator and your cluster, and gets out of the way.</p>
    </div>
    <div class="row g-5">
      <div class="col-lg-4 kv-pillar">
        <h3><i class="fas fa-shield-halved"></i> Standards-first</h3>
        <p>Kube-VIM speaks the ETSI reference points, Or-Vi and Vi-Vnfm, over both gRPC and REST with an OpenAPI client. Any ETSI-compatible NFV orchestrator can drive it, so you are not tied to a single MANO stack.</p>
      </div>
      <div class="col-lg-4 kv-pillar">
        <h3><i class="fas fa-diagram-project"></i> Kubernetes-native</h3>
        <p>It turns orchestrator requests into Kubernetes Custom Resources and manages their lifecycle, statelessly. There is no separate datastore. Every managed resource lives as a Kubernetes object in etcd.</p>
      </div>
      <div class="col-lg-4 kv-pillar">
        <h3><i class="fas fa-network-wired"></i> Truly converged</h3>
        <p>Because it reuses standard components like KubeVirt, Kube-OVN, and Multus, your VNFs share the same network and the same resource pool as your CNFs. One cluster, one fabric, no parallel infrastructure.</p>
      </div>
    </div>
  </div>
</section>

<section class="kv-oss">
  <div class="container">
    <h2>Open source, built by telco people</h2>
    <p>Kube-VIM is open source under Apache 2.0, backed and supported by Retelith, a telecom software company building Kubernetes-native infrastructure for network operators.</p>
    <a class="btn btn-light btn-lg" href="https://github.com/kube-nfv/kube-vim"><i class="fab fa-github me-2"></i> Star on GitHub</a>
  </div>
</section>
