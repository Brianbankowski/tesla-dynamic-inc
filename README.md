Tesla-Inspired-Website/ ├── public/ │   ├── models/ │   │   └── tesla-model-y.glb        # Tesla 3D model │   └── favicon.ico ├── components/ │   └── ModelViewer.js              # 3D model renderer ├── pages/ │   └── index.js                    # Main landing page ├── styles/ │   └── globals.css ├── .gitignore ├── README.md ├── package.json ├── next.config.js ├── jsconfig.json ├── .env.example


---

// components/ModelViewer.js import React, { Suspense } from 'react'; import { Canvas } from '@react-three/fiber'; import { OrbitControls, useGLTF } from '@react-three/drei';

function TeslaModel() { const gltf = useGLTF('/models/tesla-model-y.glb'); return <primitive object={gltf.scene} scale={1.2} position={[0, -1.5, 0]} />; }

export default function ModelViewer() { return ( <Canvas camera={{ position: [0, 0, 5] }}> <ambientLight intensity={1} /> <directionalLight position={[0, 5, 5]} /> <Suspense fallback={null}> <TeslaModel /> <OrbitControls enableZoom={true} /> </Suspense> </Canvas> ); }


---

// pages/index.js import Head from 'next/head'; import ModelViewer from '../components/ModelViewer'; import '../styles/globals.css';

export default function Home() { return ( <> <Head> <title>Tesla | Electric Future</title> </Head> <header className="header"> <div className="logo">TESLA</div> <nav> <ul> <li><a href="#">Model S</a></li> <li><a href="#">Model 3</a></li> <li><a href="#">Model X</a></li> <li><a href="#">Model Y</a></li> </ul> </nav> </header> <section className="hero"> <h1>Electric Power. Redefined.</h1> <p>Experience the future of mobility with Tesla's cutting-edge electric vehicles.</p> <a href="#" className="btn">Order Now</a> </section> <section className="model-section"> <ModelViewer /> </section> </> ); }


---

// styles/globals.css body { margin: 0; font-family: 'Segoe UI', sans-serif; background-color: #000; color: #fff; }

.header { display: flex; justify-content: space-between; align-items: center; padding: 1em 2em; background-color: rgba(0, 0, 0, 0.8); }

.logo { font-size: 1.5em; font-weight: bold; letter-spacing: 2px; }

nav ul { list-style: none; display: flex; gap: 2em; padding: 0; }

nav a { color: #fff; text-decoration: none; }

.hero { text-align: center; padding: 6em 2em; background: url('https://tesla-cdn.thron.com/delivery/public/image/tesla/29cdd2e8-1a09-4b74-8e83-b706e34a8c5f/bvlatuR/std/2880x1800/Homepage-Model-3-Desktop-LHD') center/cover no-repeat; }

.hero h1 { font-size: 3em; margin-bottom: 0.5em; }

.hero p { font-size: 1.2em; margin-bottom: 1.5em; }

.btn { padding: 1em 2em; background-color: #e00; color: #fff; border: none; text-transform: uppercase; font-weight: bold; text-decoration: none; border-radius: 4px; }

.model-section { height: 500px; background: #111; }


---

// package.json (minimal) { "name": "tesla-inc-clone", "version": "1.0.0", "scripts": { "dev": "next dev", "build": "next build", "start": "next start" }, "dependencies": { "next": "latest", "react": "latest", "react-dom": "latest", "@react-three/drei": "^9.76.0", "@react-three/fiber": "^8.15.6", "three": "^0.152.2" } }

