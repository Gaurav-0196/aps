<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Adarsh Public School - Badrukhan | PSEB Affiliated</title>
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Inter:opsz,wght@14..32,300;14..32,400;14..32,600;14..32,700;14..32,800;14..32,900&display=swap" rel="stylesheet">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css">
    <style>
        /* ---------- ROOT & RESET ---------- */
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        :root {
            --primary: #1a4d2e;
            --primary-light: #eaf7ef;
            --secondary: #4caf84;
            --accent: #3a9d72;
            --gold: #f5b041;
            --gold-light: #fdebd0;
            --text-dark: #1a2a1e;
            --text-muted: #4a5f4e;
            --white: #ffffff;
            --shadow: 0 8px 30px rgba(26, 77, 46, 0.10);
            --shadow-hover: 0 20px 50px rgba(26, 77, 46, 0.18);
            --radius: 18px;
            --transition: all 0.4s cubic-bezier(0.25, 0.46, 0.45, 0.94);
        }

        html {
            scroll-behavior: smooth;
        }

        body {
            font-family: 'Inter', sans-serif;
            background: var(--primary-light);
            color: var(--text-dark);
            line-height: 1.7;
            overflow-x: hidden;
            margin: 0;
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 24px;
        }

        /* ---------- SCROLL PROGRESS ---------- */
        #progressBar {
            position: fixed;
            top: 0;
            left: 0;
            height: 4px;
            background: var(--gold);
            z-index: 9999;
            width: 0%;
            transition: width 0.1s;
            box-shadow: 0 0 12px rgba(245, 176, 65, 0.5);
        }

        /* ============================================
                   PRELOADER - PREMIUM LOADING ANIMATION
                ============================================ */
        #preloader {
            position: fixed;
            inset: 0;
            background: linear-gradient(145deg, #eaf7ef 0%, #d4e8db 100%);
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            z-index: 10000;
            transition: opacity 0.8s ease, visibility 0.8s ease;
        }

        #preloader.hide {
            opacity: 0;
            visibility: hidden;
        }

        /* School Emblem in Loader */
        .loader-emblem {
            position: relative;
            width: 120px;
            height: 120px;
            background: var(--white);
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            box-shadow: 0 20px 60px rgba(26, 77, 46, 0.2), inset 0 0 0 4px var(--secondary);
            animation: emblemPulse 1.8s ease-in-out infinite;
        }

        .loader-emblem i {
            font-size: 4rem;
            color: var(--primary);
            animation: emblemSpin 2.4s cubic-bezier(0.5, 0, 0.5, 1) infinite;
        }

        .loader-emblem .badge-ring {
            position: absolute;
            inset: -8px;
            border-radius: 50%;
            border: 3px solid transparent;
            border-top-color: var(--gold);
            border-right-color: var(--secondary);
            animation: ringSpin 1.2s linear infinite;
        }

        .loader-emblem .badge-ring:nth-child(2) {
            inset: -16px;
            border-top-color: var(--secondary);
            border-right-color: var(--gold);
            animation-duration: 1.8s;
            animation-direction: reverse;
        }

        @keyframes emblemPulse {
            0%,
            100% {
                transform: scale(1);
                box-shadow: 0 20px 60px rgba(26, 77, 46, 0.2), inset 0 0 0 4px var(--secondary);
            }
            50% {
                transform: scale(1.04);
                box-shadow: 0 30px 80px rgba(26, 77, 46, 0.3), inset 0 0 0 6px var(--gold);
            }
        }

        @keyframes emblemSpin {
            0% {
                transform: rotate(0deg) scale(1);
            }
            50% {
                transform: rotate(180deg) scale(1.1);
            }
            100% {
                transform: rotate(360deg) scale(1);
            }
        }

        @keyframes ringSpin {
            0% {
                transform: rotate(0deg);
            }
            100% {
                transform: rotate(360deg);
            }
        }

        .loader-text {
            margin-top: 30px;
            font-size: 1.6rem;
            font-weight: 800;
            color: var(--primary);
            letter-spacing: 4px;
            position: relative;
        }

        .loader-text span {
            color: var(--secondary);
        }

        .loader-text .shimmer {
            background: linear-gradient(90deg, var(--primary) 0%, var(--gold) 40%, var(--secondary) 60%, var(--primary) 100%);
            background-size: 300% 100%;
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            animation: shimmerText 2.4s ease-in-out infinite;
        }

        @keyframes shimmerText {
            0% {
                background-position: 0% 50%;
            }
            50% {
                background-position: 100% 50%;
            }
            100% {
                background-position: 0% 50%;
            }
        }

        .loader-sub {
            margin-top: 8px;
            font-size: 0.85rem;
            color: var(--text-muted);
            letter-spacing: 6px;
            font-weight: 400;
            opacity: 0.7;
        }

        /* Loader Progress Bar */
        .loader-progress-wrap {
            margin-top: 28px;
            width: 220px;
            height: 4px;
            background: rgba(26, 77, 46, 0.12);
            border-radius: 10px;
            overflow: hidden;
            position: relative;
        }

        .loader-progress-wrap .loader-progress {
            height: 100%;
            width: 0%;
            background: linear-gradient(90deg, var(--secondary), var(--gold), var(--secondary));
            background-size: 200% 100%;
            border-radius: 10px;
            animation: progressGradient 1.2s ease-in-out infinite;
            transition: width 0.3s ease;
        }

        @keyframes progressGradient {
            0%,
            100% {
                background-position: 0% 50%;
            }
            50% {
                background-position: 100% 50%;
            }
        }

        .loader-percent {
            margin-top: 10px;
            font-size: 0.75rem;
            font-weight: 600;
            color: var(--text-muted);
            letter-spacing: 2px;
        }

        /* ---------- NOTICE TICKER ---------- */
        .notice-bar {
            background: var(--primary);
            color: var(--white);
            padding: 8px 0;
            overflow: hidden;
            white-space: nowrap;
            font-size: 0.85rem;
            font-weight: 500;
            border-bottom: 3px solid var(--gold);
        }
        .notice-bar .ticker {
            display: inline-block;
            animation: tickerScroll 28s linear infinite;
        }
        .notice-bar .ticker span {
            margin: 0 40px;
        }
        .notice-bar i {
            color: var(--gold);
            margin-right: 8px;
        }
        @keyframes tickerScroll {
            0% {
                transform: translateX(100%);
            }
            100% {
                transform: translateX(-100%);
            }
        }

        /* ---------- TYPOGRAPHY & BUTTONS ---------- */
        .section-title {
            font-size: 2.6rem;
            font-weight: 800;
            letter-spacing: -0.02em;
            color: var(--primary);
            text-align: center;
            margin-bottom: 12px;
        }
        .section-subtitle {
            text-align: center;
            color: var(--text-muted);
            font-size: 1.1rem;
            max-width: 700px;
            margin: 0 auto 48px;
        }
        .badge {
            display: inline-block;
            background: rgba(76, 175, 132, 0.15);
            color: var(--primary);
            padding: 6px 24px;
            border-radius: 40px;
            font-size: 0.8rem;
            font-weight: 600;
            border: 1px solid rgba(76, 175, 132, 0.3);
        }
        .badge-gold {
            background: rgba(245, 176, 65, 0.2);
            border-color: var(--gold);
            color: #7d5d1a;
        }
        .btn-primary {
            display: inline-block;
            background: var(--secondary);
            color: var(--white);
            padding: 14px 38px;
            border-radius: 50px;
            font-weight: 600;
            border: none;
            cursor: pointer;
            transition: var(--transition);
            box-shadow: 0 6px 24px rgba(76, 175, 132, 0.4);
            font-size: 1rem;
            text-decoration: none;
        }
        .btn-primary:hover {
            background: var(--accent);
            transform: translateY(-4px) scale(1.02);
            box-shadow: 0 14px 34px rgba(76, 175, 132, 0.5);
        }
        .btn-gold {
            background: var(--gold);
            box-shadow: 0 6px 24px rgba(245, 176, 65, 0.4);
        }
        .btn-gold:hover {
            background: #e09d30;
            box-shadow: 0 14px 34px rgba(245, 176, 65, 0.5);
        }
        .btn-outline {
            display: inline-block;
            background: transparent;
            color: var(--white);
            padding: 12px 34px;
            border-radius: 50px;
            font-weight: 600;
            border: 2px solid rgba(255, 255, 255, 0.8);
            transition: var(--transition);
            backdrop-filter: blur(4px);
            text-decoration: none;
        }
        .btn-outline:hover {
            background: var(--white);
            color: var(--primary);
            border-color: var(--white);
        }

        /* ---------- FLOATING LEAVES ---------- */
        .floating-leaves {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            pointer-events: none;
            z-index: -1;
            overflow: hidden;
        }
        .leaf {
            position: absolute;
            font-size: 1.8rem;
            color: rgba(76, 175, 132, 0.12);
            animation: floatLeaf linear infinite;
        }
        @keyframes floatLeaf {
            0% {
                transform: translateY(110vh) rotate(0deg) scale(0.8);
                opacity: 0;
            }
            10% {
                opacity: 1;
            }
            90% {
                opacity: 1;
            }
            100% {
                transform: translateY(-10vh) rotate(720deg) scale(1.2);
                opacity: 0;
            }
        }

        /* ============================================
                   HEADER - PREMIUM REDESIGN
                ============================================ */
        header {
            background: rgba(255, 255, 255, 0.88);
            backdrop-filter: blur(18px) saturate(180%);
            -webkit-backdrop-filter: blur(18px) saturate(180%);
            box-shadow: 0 1px 0 rgba(0, 0, 0, 0.04), 0 4px 24px rgba(26, 77, 46, 0.06);
            position: sticky;
            top: 0;
            z-index: 999;
            padding: 0;
            border-bottom: 3px solid transparent;
            background-image: linear-gradient(var(--white), var(--white)), linear-gradient(90deg, var(--secondary), var(--gold), var(--secondary));
            background-origin: padding-box, border-box;
            background-clip: padding-box, border-box;
            transition: box-shadow 0.4s ease, padding 0.3s ease;
        }

        header.scrolled {
            box-shadow: 0 8px 40px rgba(26, 77, 46, 0.12);
            background: rgba(255, 255, 255, 0.96);
        }

        nav {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 10px 0;
            transition: padding 0.3s ease;
        }

        header.scrolled nav {
            padding: 6px 0;
        }

        /* Logo Area - Premium */
        .logo {
            display: flex;
            align-items: center;
            gap: 14px;
            text-decoration: none;
            cursor: pointer;
            position: relative;
        }

        .logo-icon {
            width: 48px;
            height: 48px;
            background: linear-gradient(145deg, var(--primary), var(--secondary));
            border-radius: 14px;
            display: flex;
            align-items: center;
            justify-content: center;
            color: var(--white);
            font-size: 1.5rem;
            box-shadow: 0 4px 16px rgba(76, 175, 132, 0.3);
            transition: var(--transition);
            flex-shrink: 0;
            position: relative;
            overflow: hidden;
        }

        .logo-icon::after {
            content: '';
            position: absolute;
            inset: 0;
            background: linear-gradient(135deg, rgba(255, 255, 255, 0.25) 0%, transparent 60%);
            border-radius: 14px;
        }

        .logo:hover .logo-icon {
            transform: rotate(-6deg) scale(1.04);
            box-shadow: 0 6px 24px rgba(76, 175, 132, 0.4);
        }

        .logo-text {
            display: flex;
            flex-direction: column;
            line-height: 1.2;
        }

        .logo-text .school-name {
            font-size: 1.5rem;
            font-weight: 900;
            color: var(--primary);
            letter-spacing: -0.5px;
            display: flex;
            align-items: center;
            gap: 8px;
            flex-wrap: wrap;
        }

        .logo-text .school-name span {
            color: var(--secondary);
        }

        .logo-text .school-name .aff-tag {
            font-size: 0.55rem;
            background: linear-gradient(135deg, var(--gold), #e09d30);
            color: white;
            padding: 2px 12px;
            border-radius: 20px;
            font-weight: 700;
            letter-spacing: 0.5px;
            display: inline-block;
            box-shadow: 0 2px 8px rgba(245, 176, 65, 0.3);
        }

        .logo-text .school-name .aff-tag i {
            font-size: 0.5rem;
            margin-right: 4px;
        }

        .logo-text .school-sub {
            font-size: 0.6rem;
            font-weight: 600;
            letter-spacing: 1.5px;
            color: var(--text-muted);
            margin-top: -1px;
        }

        .logo-text .school-sub i {
            color: var(--gold);
            margin-right: 4px;
        }

        /* Underline animation on logo hover */
        .logo::after {
            content: '';
            position: absolute;
            bottom: -4px;
            left: 60px;
            right: 0;
            height: 2px;
            background: linear-gradient(90deg, var(--secondary), var(--gold));
            transform: scaleX(0);
            transform-origin: left;
            transition: transform 0.5s cubic-bezier(0.25, 0.46, 0.45, 0.94);
        }

        .logo:hover::after {
            transform: scaleX(1);
        }

        /* Navigation Links - Premium */
        .nav-links {
            display: flex;
            list-style: none;
            gap: 6px;
            align-items: center;
        }

        .nav-links a {
            font-weight: 500;
            font-size: 0.85rem;
            color: var(--text-dark);
            transition: var(--transition);
            position: relative;
            text-decoration: none;
            padding: 8px 14px;
            border-radius: 40px;
            letter-spacing: 0.2px;
        }

        .nav-links a:hover {
            color: var(--primary);
            background: rgba(76, 175, 132, 0.08);
        }

        .nav-links a::after {
            content: '';
            position: absolute;
            bottom: 4px;
            left: 50%;
            transform: translateX(-50%) scaleX(0);
            width: 60%;
            height: 2px;
            background: var(--secondary);
            border-radius: 4px;
            transition: transform 0.35s cubic-bezier(0.25, 0.46, 0.45, 0.94);
        }

        .nav-links a:hover::after {
            transform: translateX(-50%) scaleX(1);
        }

        .nav-links .nav-cta {
            padding: 8px 20px;
            font-size: 0.8rem;
            box-shadow: none;
            margin-left: 4px;
            border-radius: 40px;
            background: linear-gradient(135deg, var(--secondary), var(--accent));
        }

        .nav-links .nav-cta:hover {
            transform: translateY(-2px) scale(1.02);
            box-shadow: 0 8px 24px rgba(76, 175, 132, 0.35);
        }

        .nav-links .nav-cta i {
            margin-right: 6px;
        }

        /* Call button in nav */
        .nav-call {
            display: inline-flex;
            align-items: center;
            gap: 6px;
            font-weight: 600;
            font-size: 0.8rem;
            color: var(--primary);
            padding: 8px 14px 8px 12px;
            border-radius: 40px;
            background: rgba(245, 176, 65, 0.12);
            border: 1px solid rgba(245, 176, 65, 0.2);
            transition: var(--transition);
            text-decoration: none;
        }

        .nav-call i {
            color: var(--gold);
            font-size: 0.9rem;
        }

        .nav-call:hover {
            background: rgba(245, 176, 65, 0.2);
            border-color: var(--gold);
            transform: translateY(-2px);
        }

        /* Hamburger */
        .hamburger {
            display: none;
            flex-direction: column;
            cursor: pointer;
            gap: 5px;
            z-index: 1000;
            padding: 4px;
        }

        .hamburger span {
            width: 28px;
            height: 3px;
            background: var(--primary);
            border-radius: 4px;
            transition: var(--transition);
        }

        .hamburger.active span:nth-child(1) {
            transform: rotate(45deg) translate(6px, 6px);
        }
        .hamburger.active span:nth-child(2) {
            opacity: 0;
            transform: scaleX(0);
        }
        .hamburger.active span:nth-child(3) {
            transform: rotate(-45deg) translate(6px, -6px);
        }

        /* ---------- HERO SLIDER ---------- */
        .hero {
            position: relative;
            height: 90vh;
            min-height: 600px;
            display: flex;
            align-items: center;
            justify-content: center;
            text-align: center;
            color: var(--white);
            overflow: hidden;
        }
        .hero-slide {
            position: absolute;
            inset: 0;
            background-size: cover;
            background-position: center;
            opacity: 0;
            transition: opacity 1.2s ease;
            display: flex;
            align-items: center;
            justify-content: center;
        }
        .hero-slide.active {
            opacity: 1;
        }
        .hero-slide::after {
            content: '';
            position: absolute;
            inset: 0;
            background: rgba(18, 56, 33, 0.75);
            backdrop-filter: blur(2px);
        }
        .hero-content {
            position: relative;
            z-index: 2;
            max-width: 850px;
            padding: 20px;
        }
        .hero-content .badge-group {
            display: flex;
            flex-wrap: wrap;
            gap: 12px;
            justify-content: center;
            margin-bottom: 18px;
        }
        .hero-content .badge-group .badge {
            background: rgba(255, 255, 255, 0.12);
            color: white;
            border-color: rgba(255, 255, 255, 0.25);
            backdrop-filter: blur(4px);
            font-size: 0.8rem;
            padding: 6px 18px;
        }
        .hero-content .badge-group .badge-gold-custom {
            background: rgba(245, 176, 65, 0.25);
            border-color: var(--gold);
            color: #ffe28a;
        }
        .hero-content .motto {
            font-style: italic;
            font-weight: 300;
            font-size: 1rem;
            background: rgba(0, 0, 0, 0.2);
            display: inline-block;
            padding: 6px 28px;
            border-radius: 40px;
            margin-bottom: 16px;
            backdrop-filter: blur(4px);
            letter-spacing: 1px;
        }
        .hero-content h2 {
            font-size: 4rem;
            font-weight: 800;
            line-height: 1.1;
            letter-spacing: -0.03em;
            margin-bottom: 10px;
        }
        .hero-content h2 .highlight {
            color: #d4edda;
            text-decoration: underline;
            text-underline-offset: 12px;
            text-decoration-color: rgba(255, 255, 255, 0.4);
        }
        .hero-content .sub-heading {
            font-size: 1.2rem;
            font-weight: 400;
            background: rgba(0, 0, 0, 0.2);
            display: inline-block;
            padding: 8px 32px;
            border-radius: 60px;
            backdrop-filter: blur(4px);
            margin-bottom: 20px;
            border: 1px solid rgba(255, 255, 255, 0.1);
        }
        .hero-content .typewriter {
            font-size: 1.2rem;
            font-weight: 300;
            min-height: 3rem;
            margin-bottom: 32px;
            opacity: 0.9;
        }
        .hero-content .typewriter .cursor {
            display: inline-block;
            width: 3px;
            background: var(--gold);
            margin-left: 4px;
            animation: blink 0.8s infinite;
        }
        @keyframes blink {
            0%,
            100% {
                opacity: 1;
            }
            50% {
                opacity: 0;
            }
        }
        .hero-buttons {
            display: flex;
            gap: 20px;
            justify-content: center;
            flex-wrap: wrap;
        }
        .slider-dots {
            position: absolute;
            bottom: 30px;
            z-index: 3;
            display: flex;
            gap: 12px;
        }
        .slider-dots span {
            width: 12px;
            height: 12px;
            border-radius: 50%;
            background: rgba(255, 255, 255, 0.4);
            cursor: pointer;
            transition: var(--transition);
        }
        .slider-dots span.active {
            background: var(--gold);
            transform: scale(1.3);
            box-shadow: 0 0 16px rgba(245, 176, 65, 0.6);
        }

        /* ---------- SCROLL ANIMATIONS ---------- */
        .fade-up {
            opacity: 0;
            transform: translateY(50px);
            transition: opacity 0.8s ease, transform 0.8s ease;
        }
        .fade-up.visible {
            opacity: 1;
            transform: translateY(0);
        }
        .stagger-children>* {
            opacity: 0;
            transform: translateY(30px);
            transition: opacity 0.6s ease, transform 0.6s ease;
        }
        .stagger-children.visible>*:nth-child(1) {
            transition-delay: 0.05s;
        }
        .stagger-children.visible>*:nth-child(2) {
            transition-delay: 0.15s;
        }
        .stagger-children.visible>*:nth-child(3) {
            transition-delay: 0.25s;
        }
        .stagger-children.visible>*:nth-child(4) {
            transition-delay: 0.35s;
        }
        .stagger-children.visible>* {
            opacity: 1;
            transform: translateY(0);
        }

        /* ---------- CARDS ---------- */
        .grid-4 {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
            gap: 30px;
            margin-top: 20px;
        }
        .card-glass {
            background: rgba(255, 255, 255, 0.7);
            backdrop-filter: blur(8px);
            padding: 30px 20px;
            text-align: center;
            border-radius: var(--radius);
            box-shadow: var(--shadow);
            transition: var(--transition);
            border: 1px solid rgba(255, 255, 255, 0.8);
        }
        .card-glass:hover {
            transform: translateY(-12px) scale(1.02);
            box-shadow: var(--shadow-hover);
            background: var(--white);
        }
        .card-glass i {
            font-size: 2.8rem;
            color: var(--secondary);
            margin-bottom: 12px;
        }
        .card-glass h4 {
            font-size: 1.2rem;
            margin-bottom: 6px;
            color: var(--primary);
        }
        .card-glass p {
            color: var(--text-muted);
            font-size: 0.9rem;
        }

        /* ---------- ABOUT ---------- */
        #about {
            background: var(--white);
            padding: 80px 0;
        }
        .about-grid {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 60px;
            align-items: center;
        }
        .about-image {
            position: relative;
            border-radius: var(--radius);
            overflow: hidden;
            box-shadow: var(--shadow);
        }
        .about-image img {
            width: 100%;
            display: block;
            transition: var(--transition);
        }
        .about-image:hover img {
            transform: scale(1.05);
        }
        .about-image .floating-badge {
            position: absolute;
            bottom: -10px;
            right: -10px;
            background: var(--gold);
            color: white;
            padding: 12px 28px;
            border-radius: 50px;
            font-weight: 700;
            box-shadow: 0 8px 24px rgba(245, 176, 65, 0.4);
        }
        .about-content h3 {
            font-size: 2.2rem;
            color: var(--primary);
            margin-bottom: 12px;
        }
        .about-content h3 span {
            color: var(--secondary);
        }
        .about-content .aff-num {
            background: var(--primary-light);
            padding: 8px 20px;
            border-radius: 40px;
            display: inline-block;
            font-weight: 600;
            color: var(--primary);
            border: 1px dashed var(--secondary);
            margin-bottom: 16px;
            font-size: 0.9rem;
        }
        .about-content p {
            color: var(--text-muted);
            margin-bottom: 16px;
        }
        .stat-box {
            display: flex;
            gap: 30px;
            background: var(--primary-light);
            padding: 20px 30px;
            border-radius: var(--radius);
            margin-top: 20px;
            flex-wrap: wrap;
        }
        .stat-box div {
            text-align: center;
            flex: 1;
        }
        .stat-box div h4 {
            font-size: 2rem;
            color: var(--primary);
            font-weight: 800;
        }
        .stat-box div p {
            margin: 0;
            font-size: 0.85rem;
        }

        /* ---------- PRINCIPAL'S DESK ---------- */
        #principal {
            background: var(--primary-light);
            padding: 80px 0;
        }
        .principal-wrap {
            display: flex;
            gap: 50px;
            align-items: center;
            background: var(--white);
            padding: 40px;
            border-radius: var(--radius);
            box-shadow: var(--shadow);
        }
        .principal-wrap img {
            width: 180px;
            height: 180px;
            border-radius: 50%;
            object-fit: cover;
            border: 6px solid var(--secondary);
            flex-shrink: 0;
        }
        .principal-wrap blockquote {
            font-size: 1.2rem;
            font-style: italic;
            color: var(--text-muted);
            border-left: 5px solid var(--gold);
            padding-left: 25px;
        }
        .principal-wrap blockquote .name {
            font-style: normal;
            font-weight: 700;
            color: var(--primary);
            margin-top: 10px;
            display: block;
        }

        /* ---------- ACADEMICS ---------- */
        #academics {
            background: var(--white);
            padding: 80px 0;
        }
        .academics-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(260px, 1fr));
            gap: 30px;
        }
        .academic-card {
            background: var(--primary-light);
            padding: 30px;
            border-radius: var(--radius);
            border-left: 6px solid var(--secondary);
            transition: var(--transition);
        }
        .academic-card:hover {
            transform: translateY(-6px);
            box-shadow: var(--shadow);
            background: var(--white);
        }
        .academic-card h4 {
            font-size: 1.4rem;
            color: var(--primary);
        }
        .academic-card .gender-tag {
            font-size: 0.7rem;
            background: var(--gold);
            color: white;
            padding: 2px 14px;
            border-radius: 20px;
            display: inline-block;
            margin-top: 6px;
        }

        /* ---------- FACILITIES ---------- */
        #facilities {
            background: var(--white);
            padding: 80px 0;
        }

        /* ---------- GALLERY LIGHTBOX ---------- */
        #gallery {
            background: var(--primary-light);
            padding: 80px 0;
        }
        .gallery-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
            gap: 24px;
        }
        .gallery-grid .gallery-item {
            height: 200px;
            border-radius: var(--radius);
            background-size: cover;
            background-position: center;
            cursor: pointer;
            position: relative;
            overflow: hidden;
            border: 3px solid transparent;
            transition: var(--transition);
            display: flex;
            align-items: center;
            justify-content: center;
            color: white;
            font-weight: 600;
            font-size: 1.2rem;
            text-shadow: 0 2px 10px rgba(0, 0, 0, 0.5);
        }
        .gallery-grid .gallery-item:hover {
            transform: scale(1.05);
            border-color: var(--gold);
        }
        .gallery-grid .gallery-item .overlay {
            background: rgba(0, 0, 0, 0.3);
            padding: 12px 20px;
            border-radius: 40px;
            backdrop-filter: blur(4px);
        }
        .lightbox {
            position: fixed;
            inset: 0;
            background: rgba(0, 0, 0, 0.92);
            z-index: 9999;
            display: flex;
            align-items: center;
            justify-content: center;
            opacity: 0;
            visibility: hidden;
            transition: var(--transition);
            backdrop-filter: blur(8px);
        }
        .lightbox.active {
            opacity: 1;
            visibility: visible;
        }
        .lightbox img {
            max-height: 80vh;
            max-width: 90vw;
            border-radius: var(--radius);
            box-shadow: 0 20px 60px rgba(0, 0, 0, 0.6);
            border: 3px solid rgba(255, 255, 255, 0.1);
        }
        .lightbox .close-lb {
            position: absolute;
            top: 30px;
            right: 40px;
            font-size: 2.5rem;
            color: white;
            cursor: pointer;
            transition: var(--transition);
        }
        .lightbox .close-lb:hover {
            transform: rotate(90deg);
            color: var(--gold);
        }
        .lightbox .nav-lb {
            position: absolute;
            top: 50%;
            transform: translateY(-50%);
            background: rgba(255, 255, 255, 0.1);
            border: none;
            color: white;
            font-size: 2rem;
            padding: 16px 20px;
            cursor: pointer;
            border-radius: 50%;
            transition: var(--transition);
            backdrop-filter: blur(4px);
        }
        .lightbox .nav-lb:hover {
            background: var(--gold);
            color: black;
        }
        .lightbox .prev-lb {
            left: 20px;
        }
        .lightbox .next-lb {
            right: 20px;
        }

        /* ---------- TRANSPORT & TIMINGS ---------- */
        #transport {
            background: var(--white);
            padding: 80px 0;
        }
        .info-grid {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 40px;
        }
        .info-card {
            background: var(--primary-light);
            padding: 30px;
            border-radius: var(--radius);
            box-shadow: var(--shadow);
            border-top: 6px solid var(--secondary);
        }
        .info-card h4 {
            font-size: 1.4rem;
            color: var(--primary);
            margin-bottom: 12px;
        }
        .info-card ul {
            list-style: none;
        }
        .info-card ul li {
            padding: 8px 0;
            border-bottom: 1px solid rgba(0, 0, 0, 0.04);
            display: flex;
            gap: 12px;
            align-items: center;
        }
        .info-card ul li i {
            color: var(--gold);
            width: 20px;
        }

        /* ---------- TESTIMONIALS ---------- */
        #testimonials {
            background: var(--primary-light);
            padding: 80px 0;
        }
        .testimonial-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(260px, 1fr));
            gap: 30px;
        }
        .testimonial-card {
            background: var(--white);
            padding: 30px;
            border-radius: var(--radius);
            box-shadow: var(--shadow);
            transition: var(--transition);
        }
        .testimonial-card:hover {
            transform: scale(1.02);
        }
        .testimonial-card i.fa-quote-left {
            font-size: 2rem;
            color: var(--secondary);
            opacity: 0.3;
            margin-bottom: 10px;
        }
        .testimonial-card p {
            font-style: italic;
            color: var(--text-muted);
        }
        .testimonial-card .author {
            margin-top: 16px;
            font-weight: 700;
            color: var(--primary);
        }

        /* ---------- CONTACT ---------- */
        #contact {
            background: var(--white);
            padding: 80px 0;
        }
        .contact-wrapper {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 50px;
        }
        .contact-info h3 {
            font-size: 1.8rem;
            color: var(--primary);
            margin-bottom: 20px;
        }
        .contact-detail {
            display: flex;
            align-items: center;
            gap: 18px;
            margin-bottom: 22px;
        }
        .contact-detail i {
            width: 48px;
            height: 48px;
            background: var(--primary-light);
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            color: var(--secondary);
            font-size: 1.2rem;
            flex-shrink: 0;
        }
        .contact-detail strong {
            display: block;
            font-size: 0.8rem;
            color: var(--text-muted);
            text-transform: uppercase;
            letter-spacing: 0.5px;
        }
        .contact-form input,
        .contact-form select,
        .contact-form textarea {
            width: 100%;
            padding: 16px 20px;
            border: 1.5px solid #e2efe6;
            border-radius: 12px;
            margin-bottom: 18px;
            font-family: inherit;
            transition: var(--transition);
            background: var(--primary-light);
            font-size: 1rem;
        }
        .contact-form input:focus,
        .contact-form select:focus,
        .contact-form textarea:focus {
            outline: none;
            border-color: var(--secondary);
            background: var(--white);
            box-shadow: 0 0 0 5px rgba(76, 175, 132, 0.15);
        }
        .contact-form textarea {
            height: 120px;
            resize: vertical;
        }

        /* ---------- FLOATING CTA ---------- */
        .float-wa {
            position: fixed;
            bottom: 90px;
            right: 24px;
            z-index: 998;
            display: flex;
            flex-direction: column;
            gap: 12px;
        }
        .float-wa a {
            width: 56px;
            height: 56px;
            border-radius: 50%;
            background: #25d366;
            color: white;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 2rem;
            box-shadow: 0 6px 24px rgba(37, 211, 102, 0.4);
            transition: var(--transition);
            text-decoration: none;
        }
        .float-wa a:hover {
            transform: scale(1.1) translateY(-4px);
        }
        .float-wa .call {
            background: var(--primary);
            box-shadow: 0 6px 24px rgba(26, 77, 46, 0.4);
        }

        /* ---------- FOOTER ---------- */
        footer {
            background: var(--primary);
            color: rgba(255, 255, 255, 0.85);
            padding: 50px 0 20px;
            text-align: center;
        }
        footer .logo h1 {
            color: var(--white);
        }
        footer .logo span {
            color: #a3d9b1;
        }
        footer .logo .aff-tag {
            background: var(--gold);
        }
        footer .logo p {
            color: rgba(255, 255, 255, 0.6);
        }
        .footer-links {
            display: flex;
            justify-content: center;
            gap: 30px;
            flex-wrap: wrap;
            margin: 20px 0 25px;
        }
        .footer-links a {
            font-weight: 500;
            transition: var(--transition);
            text-decoration: none;
            color: rgba(255, 255, 255, 0.8);
        }
        .footer-links a:hover {
            color: var(--gold);
        }
        .social-icons a {
            display: inline-block;
            width: 42px;
            height: 42px;
            background: rgba(255, 255, 255, 0.08);
            border-radius: 50%;
            line-height: 42px;
            margin: 0 8px;
            transition: var(--transition);
            color: var(--white);
            text-decoration: none;
        }
        .social-icons a:hover {
            background: var(--gold);
            transform: translateY(-4px);
            color: var(--primary);
        }
        .copyright {
            border-top: 1px solid rgba(255, 255, 255, 0.1);
            padding-top: 22px;
            margin-top: 28px;
            font-size: 0.9rem;
            opacity: 0.8;
        }

        /* ---------- RESPONSIVE ---------- */
        @media (max-width: 992px) {
            .about-grid,
            .contact-wrapper,
            .principal-wrap,
            .info-grid {
                grid-template-columns: 1fr;
            }
            .principal-wrap {
                text-align: center;
                flex-direction: column;
            }
            .principal-wrap blockquote {
                border-left: none;
                border-top: 5px solid var(--gold);
                padding-top: 20px;
                padding-left: 0;
            }
            .hero-content h2 {
                font-size: 3rem;
            }
            .about-image .floating-badge {
                display: none;
            }
            .nav-call {
                display: none;
            }
            .logo-text .school-name {
                font-size: 1.2rem;
            }
            .logo-icon {
                width: 40px;
                height: 40px;
                font-size: 1.2rem;
            }
        }

        @media (max-width: 768px) {
            .hamburger {
                display: flex;
            }
            .nav-links {
                position: fixed;
                top: 0;
                right: -100%;
                width: 80%;
                max-width: 320px;
                height: 100vh;
                background: var(--white);
                flex-direction: column;
                padding: 80px 30px 30px;
                gap: 10px;
                transition: 0.4s cubic-bezier(0.22, 1, 0.36, 1);
                box-shadow: -10px 0 40px rgba(0, 0, 0, 0.08);
                align-items: stretch;
                border-left: 4px solid var(--secondary);
            }
            .nav-links.active {
                right: 0;
            }
            .nav-links a {
                padding: 12px 16px;
                border-radius: 12px;
                font-size: 0.95rem;
            }
            .nav-links a::after {
                display: none;
            }
            .nav-links a:hover {
                background: rgba(76, 175, 132, 0.08);
            }
            .nav-links .nav-cta {
                margin-left: 0;
                text-align: center;
                margin-top: 8px;
            }
            .hero {
                height: 80vh;
                min-height: 500px;
            }
            .hero-content h2 {
                font-size: 2.2rem;
            }
            .hero-content .sub-heading {
                font-size: 0.9rem;
                padding: 4px 16px;
            }
            .section-title {
                font-size: 2rem;
            }
            .stat-box {
                flex-direction: column;
                align-items: center;
                gap: 10px;
            }
            .lightbox .nav-lb {
                font-size: 1.2rem;
                padding: 10px 14px;
            }
            .lightbox .prev-lb {
                left: 10px;
            }
            .lightbox .next-lb {
                right: 10px;
            }
            .loader-emblem {
                width: 90px;
                height: 90px;
            }
            .loader-emblem i {
                font-size: 3rem;
            }
            .loader-text {
                font-size: 1.2rem;
            }
            .logo-text .school-name {
                font-size: 1rem;
            }
            .logo-text .school-name .aff-tag {
                font-size: 0.45rem;
                padding: 1px 8px;
            }
            .logo-icon {
                width: 36px;
                height: 36px;
                font-size: 1rem;
                border-radius: 10px;
            }
            .logo-text .school-sub {
                font-size: 0.5rem;
            }
        }

        @media (max-width: 480px) {
            .hero-content h2 {
                font-size: 1.7rem;
            }
            .float-wa {
                right: 12px;
                bottom: 80px;
            }
            .float-wa a {
                width: 46px;
                height: 46px;
                font-size: 1.6rem;
            }
            .logo-text .school-name {
                font-size: 0.85rem;
            }
            .logo-icon {
                width: 32px;
                height: 32px;
                font-size: 0.85rem;
                border-radius: 8px;
            }
            .logo {
                gap: 10px;
            }
        }
    </style>
</head>
<body>

    <!-- ============================================
    PRELOADER - PREMIUM LOADING ANIMATION
    ============================================ -->
    <div id="preloader">
        <div class="loader-emblem">
            <i class="fas fa-book-open"></i>
            <span class="badge-ring"></span>
            <span class="badge-ring"></span>
        </div>
        <div class="loader-text">
            <span class="shimmer">Adarsh Public School</span>
        </div>
        <div class="loader-sub">— BADRUKHAN —</div>
        <div class="loader-progress-wrap">
            <div class="loader-progress" id="loaderProgress"></div>
        </div>
        <div class="loader-percent" id="loaderPercent">0%</div>
    </div>

    <!-- SCROLL PROGRESS -->
    <div id="progressBar"></div>

    <!-- FLOATING LEAVES -->
    <div class="floating-leaves" id="leafContainer"></div>

    <!-- NOTICE BAR -->
    <div class="notice-bar">
        <div class="ticker">
            <span><i class="fas fa-bullhorn"></i> Admissions Open 2026-27 | PSEB Affil. No. 2170174</span>
            <span><i class="fas fa-users"></i> Nursery to 10th (Boys) | Nursery to 12th (Girls)</span>
            <span><i class="fas fa-bus"></i> School Bus Facility Available</span>
            <span><i class="fas fa-tree"></i> Open-Air Eco-Friendly Campus</span>
            <span><i class="fas fa-bullhorn"></i> Admissions Open 2026-27 | PSEB Affil. No. 2170174</span>
        </div>
    </div>

    <!-- ============================================
    HEADER - PREMIUM REDESIGN
    ============================================ -->
    <header id="mainHeader">
        <div class="container">
            <nav>
                <a href="#home" class="logo">
                    <div class="logo-icon">
                        <i class="fas fa-book-open"></i>
                    </div>
                    <div class="logo-text">
                        <div class="school-name">
                            Adarsh <span>Public</span>
                            <span class="aff-tag"><i class="fas fa-id-card"></i> PSEB</span>
                        </div>
                        <div class="school-sub">
                            <i class="fas fa-map-pin"></i> BADRUKHAN · AFFIL. NO. 2170174
                        </div>
                    </div>
                </a>

                <ul class="nav-links" id="navLinks">
                    <li><a href="#home">Home</a></li>
                    <li><a href="#about">About</a></li>
                    <li><a href="#academics">Academics</a></li>
                    <li><a href="#gallery">Gallery</a></li>
                    <li><a href="#contact">Contact</a></li>
                    <li>
                        <a href="tel:+919876543210" class="nav-call">
                            <i class="fas fa-phone"></i> Call
                        </a>
                    </li>
                    <li>
                        <a href="#contact" class="btn-primary nav-cta">
                            <i class="fas fa-user-plus"></i> Enroll
                        </a>
                    </li>
                </ul>

                <div class="hamburger" id="hamburger">
                    <span></span>
                    <span></span>
                    <span></span>
                </div>
            </nav>
        </div>
    </header>

    <!-- ============================================
    HERO SLIDER
    ============================================ -->
    <section class="hero" id="home">
        <div class="hero-slide active" style="background-image: url('https://images.unsplash.com/photo-1509062522246-3755977927d7?ixlib=rb-4.0.3&auto=format&fit=crop&w=1920&q=80');">
            <div class="hero-content">
                <div class="badge-group">
                    <span class="badge"><i class="fas fa-seedling"></i> Admissions 2026-27</span>
                    <span class="badge badge-gold-custom"><i class="fas fa-id-card"></i> Affil. 2170174</span>
                </div>
                <div class="motto">🌿 "Gyan, Shraddha, Seva" — Knowledge, Faith, Service</div>
                <h2>Growing Minds in <span class="highlight">Badrukhan</span></h2>
                <div class="sub-heading"><i class="fas fa-venus-mars"></i> Nursery-10th (Boys) | Nursery-12th (Girls)</div>
                <div class="typewriter"><span id="typedText"></span><span class="cursor"></span></div>
                <div class="hero-buttons">
                    <a href="#contact" class="btn-primary btn-gold"><i class="fas fa-graduation-cap"></i> Enroll Now</a>
                    <a href="#about" class="btn-outline">Explore Campus</a>
                </div>
            </div>
        </div>
        <div class="hero-slide" style="background-image: url('https://images.unsplash.com/photo-1580582932707-520aed937b7b?ixlib=rb-4.0.3&auto=format&fit=crop&w=1920&q=80');">
            <div class="hero-content">
                <div class="badge-group">
                    <span class="badge"><i class="fas fa-chalkboard-teacher"></i> PSEB Curriculum</span>
                    <span class="badge badge-gold-custom"><i class="fas fa-bus"></i> Bus Facility</span>
                </div>
                <div class="motto">🌱 Empowering Rural India</div>
                <h2>Affordable <span class="highlight">Quality</span> Education</h2>
                <div class="sub-heading"><i class="fas fa-school"></i> Open-Air Building · Playground</div>
                <div class="typewriter"><span>Where every child's future shines bright.</span><span class="cursor"></span></div>
                <div class="hero-buttons">
                    <a href="#about" class="btn-primary"><i class="fas fa-"></i> About</a>
                </div>
            </div>
        </div>
        <div class="hero-slide" style="background-image: url('https://images.unsplash.com/photo-1571260899304-425eee4c7efc?ixlib=rb-4.0.3&auto=format&fit=crop&w=1920&q=80');">
            <div class="hero-content">
                <div class="badge-group">
                    <span class="badge"><i class="fas fa-tree"></i> Green Campus</span>
                    <span class="badge badge-gold-custom"><i class="fas fa-futbol"></i> Sports Ground</span>
                </div>
                <div class="motto">🌸 Where nature meets knowledge</div>
                <h2>A <span class="highlight">Green</span> School for the Future</h2>
                <div class="sub-heading"><i class="fas fa-wind"></i> Open-Air Classrooms</div>
                <div class="typewriter"><span>Learning in harmony with nature.</span><span class="cursor"></span></div>
                <div class="hero-buttons">
                    <a href="#gallery" class="btn-primary btn-gold"><i class="fas fa-camera"></i> View Gallery</a>
                </div>
            </div>
        </div>
        <div class="slider-dots" id="sliderDots">
            <span class="active" data-index="0"></span>
            <span data-index="1"></span>
            <span data-index="2"></span>
        </div>
    </section>

    <!-- WHY CHOOSE US -->
    <section style="padding: 60px 0 40px; background: var(--white);">
        <div class="container">
            <div class="grid-4 stagger-children" id="staggerWhy">
                <div class="card-glass"><i class="fas fa-chalkboard-teacher"></i><h4>PSEB Affiliated</h4><p>Affiliation No. 2170174. Standardized curriculum.</p></div>
                <div class="card-glass"><i class="fas fa-child"></i><h4>Boys & Girls</h4><p>Nursery-10th (Boys) | Nursery-12th (Girls).</p></div>
                <div class="card-glass"><i class="fas fa-tree"></i><h4>Open-Air Campus</h4><p>Eco-friendly, naturally ventilated classrooms.</p></div>
                <div class="card-glass"><i class="fas fa-futbol"></i><h4>Playground</h4><p>Dedicated safe playground for kids' recreation.</p></div>
            </div>
        </div>
    </section>

    <!-- ABOUT -->
    <section id="about">
        <div class="container">
            <div class="about-grid">
                <div class="about-image fade-up">
                    <img src="https://i.postimg.cc/hhWVM0FS/Whats-App-Image-2026-07-05-at-5-48-05-PM.jpg" alt="School">
                </div>
                <div class="about-content fade-up">
                    <span class="badge" style="margin-bottom: 8px;">About Us</span>
                    <h3>Welcome to <span>Adarsh Public School</span></h3>
                    <div class="aff-num"><i class="fas fa-id-card"></i> PSEB Affil. No. 2170174</div>
                    <p>Located in the heart of <strong>Village Badrukhan</strong>, our school offers a unique blend of modern education and rural values. We are proud to offer <strong>Nursery to 10th for Boys</strong> and <strong>Nursery to 12th for Girls</strong>, following the PSEB pattern.</p>
                    <p>Our <strong>open-air building</strong> ensures fresh air and natural light, while our <strong>playground</strong> and <strong>school bus service</strong> make learning safe and joyful. We believe in providing <strong>affordable fees</strong> without compromising on quality.</p>
                    <div class="stat-box">
                        <div><h4 id="statYears">0</h4><p>Years of Trust</p></div>
                        <div><h4 id="statStudents">0</h4><p>Students Enrolled</p></div>
                        <div><h4 id="statSatisfaction">0</h4><p>Trusted Parents</p></div>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- ACADEMICS -->
    <section id="academics">
        <div class="container">
            <h2 class="section-title fade-up">Our Academic Structure</h2>
            <p class="section-subtitle fade-up">PSEB Pattern curriculum designed for holistic development.</p>
            <div class="academics-grid">
                <div class="academic-card fade-up">
                    <h4>🌱 Primary (Nursery - 5)</h4>
                    <p>Foundation years with play-way methods, storytelling, and basic literacy & numeracy.</p>
                    <span class="gender-tag"><i class="fas fa-venus-mars"></i> Boys & Girls</span>
                </div>
                <div class="academic-card fade-up">
                    <h4>📘 Middle (6 - 8)</h4>
                    <p>Core subjects: Math, Science, English, Hindi, Social Studies, and Computer basics.</p>
                    <span class="gender-tag"><i class="fas fa-venus-mars"></i> Boys & Girls</span>
                </div>
                <div class="academic-card fade-up">
                    <h4>📚 Secondary (9 - 10)</h4>
                    <p>In-depth PSEB syllabus with career counseling and competitive exam orientation.</p>
                    <span class="gender-tag"><i class="fas fa-male"></i> Only Boys</span>
                </div>
                <div class="academic-card fade-up">
                    <h4>📖 Sr. Secondary (11 - 12)</h4>
                    <p>Specialized streams (Arts/Commerce/Science) for higher education readiness.</p>
                    <span class="gender-tag"><i class="fas fa-female"></i> Only Girls</span>
                </div>
            </div>
        </div>
    </section>

    <!-- FACILITIES -->
    <section id="facilities">
        <div class="container">
            <h2 class="section-title fade-up">Our Special Facilities</h2>
            <p class="section-subtitle fade-up">Everything designed keeping your child's safety, health, and growth in mind.</p>
            <div class="grid-4 stagger-children" id="staggerFacilities">
                <div class="card-glass"><i class="fas fa-tree"></i><h4>Open-Air Building</h4><p>Eco-friendly design with maximum ventilation and natural light.</p></div>
                <div class="card-glass"><i class="fas fa-futbol"></i><h4>Kids Playground</h4><p>Safe, well-equipped play area for physical development and fun.</p></div>
                <div class="card-glass"><i class="fas fa-bus-alt"></i><h4>School Bus Service</h4><p>Reliable transport covering Badrukhan and 10+ nearby villages.</p></div>
                <div class="card-glass"><i class="fas fa-hand-holding-usd"></i><h4>Affordable Fees</h4><p>Lowest fee structure in the region with easy payment options.</p></div>
                <div class="card-glass"><i class="fas fa-laptop"></i><h4>Smart Classes</h4><p>Digital boards and e-learning resources for modern teaching.</p></div>
                <div class="card-glass"><i class="fas fa-shield-alt"></i><h4>Safe Campus</h4><p>24/7 security, CCTV surveillance, and strict anti-bullying policies.</p></div>
            </div>
        </div>
    </section>

    <!-- TRANSPORT & TIMINGS -->
    <section id="transport">
        <div class="container">
            <h2 class="section-title fade-up">School Timings & Transport</h2>
            <p class="section-subtitle fade-up">Structured schedules for maximum learning and convenience.</p>
            <div class="info-grid">
                <div class="info-card fade-up">
                    <h4><i class="fas fa-clock" style="color:var(--gold);"></i> School Timings</h4>
                    <ul>
                        <li><i class="fas fa-calendar-day"></i> Monday - Saturday</li>
                        <li><i class="fas fa-hourglass-start"></i> Morning Assembly: 8:20 AM</li>
                        <li><i class="fas fa-chalkboard"></i> First Bell: 9:00 AM</li>
                        <li><i class="fas fa-hourglass-end"></i> Dismissal: 1:20 - 2:30 PM</li>
                        <li><i class="fas fa-calendar-alt"></i> Sunday & 2nd Saturday: Closed</li>
                    </ul>
                </div>
                <div class="info-card fade-up">
                    <h4><i class="fas fa-bus" style="color:var(--gold);"></i> Bus Routes</h4>
                    <ul>
                        <li><i class="fas fa-route"></i> Route 1: Badrukhan - Bahadurpur - Duggan - Bhamabadi</li>
                        <li><i class="fas fa-route"></i> Route 2: Badrukhan - 1st Route</li>
                        <li><i class="fas fa-route"></i> Route 3: Badrukhan - 2nd Route</li>
                        <li><i class="fas fa-route"></i> Route 4: Badrukhan - Ubbawal</li>
                        <li><i class="fas fa-clock"></i> Pickup starts at 7:00 - 8:30 AM</li>
                    </ul>
                </div>
            </div>
        </div>
    </section>

    <!-- LIGHTBOX -->
    <div class="lightbox" id="lightbox">
        <span class="close-lb" id="closeLb">&times;</span>
        <button class="nav-lb prev-lb" id="prevLb"><i class="fas fa-chevron-left"></i></button>
        <img src="" alt="Gallery" id="lbImage">
        <button class="nav-lb next-lb" id="nextLb"><i class="fas fa-chevron-right"></i></button>
    </div>

    <!-- CONTACT -->
    <section id="contact" style="background: var(--primary-light);">
        <div class="container">
            <h2 class="section-title fade-up">Get In Touch</h2>
            <p class="section-subtitle fade-up">Visit our open-air campus or call us for any queries.</p>
            <div class="contact-wrapper">
                <div class="contact-info fade-up">
                    <h3>📍 Adarsh Public School</h3>
                    <div class="contact-detail"><i class="fas fa-map-pin"></i><div><strong>Address</strong>Village Badrukhan ( Sangrur )</div></div>
                    <div class="contact-detail"><i class="fas fa-phone-alt"></i><div><strong>Call Us</strong>+91 82645 27009 <br> +91 98728 67633</div></div>
                    <div class="contact-detail"><i class="fas fa-envelope"></i><div><strong>Email</strong>adarshpublicschoolbadrukhan@gmail.com</div></div>
                    <div class="contact-detail"><i class="fas fa-id-card"></i><div><strong>PSEB Affil. No.</strong>2170174</div></div>
                    <div class="contact-detail"><i class="fas fa-clock"></i><div><strong>Office Hours</strong>Mon - Sat: 7:00 AM – 2:30 PM</div></div>
                </div>
                <div class="fade-up">
                    <form class="contact-form" id="contactForm">
                        <input type="text" placeholder="Full Name" required>
                        <input type="email" placeholder="Email Address" required>
                        <select required>
                            <option value="">Select Class Seeking Admission</option>
                            <option>Nursery to 5th (Boys & Girls)</option>
                            <option>6th to 8th (Boys & Girls)</option>
                            <option>9th to 10th (Only Boys)</option>
                            <option>11th to 12th (Only Girls)</option>
                        </select>
                        <textarea placeholder="Write your message..."></textarea>
                        <button type="submit" class="btn-primary btn-gold" style="width:100%;"><i class="fas fa-paper-plane"></i> Send Enquiry</button>
                    </form>
                </div>
            </div>
        </div>
    </section>

    <!-- FLOATING WHATSAPP & CALL -->
    <div class="float-wa">
        <a href="tel:+918264527009" class="call" aria-label="Call"><i class="fas fa-phone"></i></a>
        <a href="https://wa.me/9872867633" target="_blank" aria-label="WhatsApp"><i class="fab fa-whatsapp"></i></a>
    </div>

    <!-- FOOTER -->
    <footer>
        <div class="container">
            <div class="logo" style="margin-bottom:6px; justify-content:center; cursor:default;">
                <div class="logo-icon" style="background: linear-gradient(145deg, #2d6b43, #5cbf94);">
                    <i class="fas fa-book-open"></i>
                </div>
                <div class="logo-text" style="text-align:left;">
                    <div class="school-name" style="color:var(--white);">
                        Adarsh <span style="color:#a3d9b1;">Public</span>
                        <span class="aff-tag" style="background:var(--gold);"><i class="fas fa-id-card"></i> PSEB</span>
                    </div>
                    <div class="school-sub" style="color:rgba(255,255,255,0.6);">
                        <i class="fas fa-map-pin"></i> BADRUKHAN · AFFIL. NO. 2170174
                    </div>
                </div>
            </div>
            <div class="footer-links">
                <a href="#home">Home</a><a href="#about">About</a><a href="#academics">Academics</a>
                <a href="#gallery">Gallery</a><a href="#contact">Contact</a>
            </div>
            <div class="social-icons">
                <a href="https://www.facebook.com/people/Adarsh-Public-School-Badrukhan/61580999720061/"><i class="fab fa-facebook-f"></i></a>
                <a href="https://www.instagram.com/adarsh.publicschool1?igsh=MXM3MWRkMmQ0amI5bw=="><i class="fab fa-instagram"></i></a>
            </div>
            <div class="copyright">
                &copy; <span id="year"></span> Adarsh Public School, Badrukhan. All Rights Reserved. <br>
                <span style="font-size:0.8rem;">Designed with <i class="fas fa-heart" style="color:#ff6b6b;"></i> for our village community. | PSEB Affil. 2170174</span>
            </div>
        </div>
    </footer>

    <script>
        // ============================================
        // PRELOADER WITH PROGRESS BAR
        // ============================================
        (function() {
            const preloader = document.getElementById('preloader');
            const progressBar = document.getElementById('loaderProgress');
            const percentText = document.getElementById('loaderPercent');
            let progress = 0;

            // Simulate loading progress
            const interval = setInterval(() => {
                // Random increment between 2-8%
                const increment = 2 + Math.random() * 6;
                progress = Math.min(progress + increment, 99);
                progressBar.style.width = progress + '%';
                percentText.textContent = Math.floor(progress) + '%';
            }, 120);

            // When window fully loads, complete the progress and hide preloader
            window.addEventListener('load', function() {
                clearInterval(interval);
                progress = 100;
                progressBar.style.width = '100%';
                percentText.textContent = '100%';

                // Small delay before hiding for smooth transition
                setTimeout(() => {
                    preloader.classList.add('hide');
                }, 400);
            });

            // Fallback: if something fails to load, hide after 6 seconds max
            setTimeout(() => {
                if (!preloader.classList.contains('hide')) {
                    progress = 100;
                    progressBar.style.width = '100%';
                    percentText.textContent = '100%';
                    setTimeout(() => {
                        preloader.classList.add('hide');
                    }, 300);
                }
            }, 6000);
        })();

        // ---------- SCROLL PROGRESS ----------
        window.addEventListener('scroll', () => {
            const winScroll = document.documentElement.scrollTop;
            const height = document.documentElement.scrollHeight - document.documentElement.clientHeight;
            document.getElementById('progressBar').style.width = (winScroll / height) * 100 + '%';
        });

        // ---------- HEADER SCROLL EFFECT ----------
        const header = document.getElementById('mainHeader');
        window.addEventListener('scroll', () => {
            if (window.scrollY > 30) {
                header.classList.add('scrolled');
            } else {
                header.classList.remove('scrolled');
            }
        });

        // ---------- FLOATING LEAVES ----------
        const leafContainer = document.getElementById('leafContainer');
        const leaves = ['🍃', '🌿', '☘️', '🍀'];
        for (let i = 0; i < 14; i++) {
            const el = document.createElement('div');
            el.className = 'leaf';
            el.textContent = leaves[i % leaves.length];
            el.style.left = Math.random() * 100 + '%';
            el.style.fontSize = (1.0 + Math.random() * 1.8) + 'rem';
            el.style.animationDuration = (18 + Math.random() * 28) + 's';
            el.style.animationDelay = (Math.random() * 22) + 's';
            leafContainer.appendChild(el);
        }

        // ---------- HERO SLIDER ----------
        let slideIndex = 0;
        const slides = document.querySelectorAll('.hero-slide');
        const dots = document.querySelectorAll('.slider-dots span');

        function showSlide(index) {
            slides.forEach((s, i) => s.classList.toggle('active', i === index));
            dots.forEach((d, i) => d.classList.toggle('active', i === index));
        }

        function nextSlide() {
            slideIndex = (slideIndex + 1) % slides.length;
            showSlide(slideIndex);
        }
        dots.forEach(d => {
            d.addEventListener('click', () => {
                slideIndex = parseInt(d.dataset.index);
                showSlide(slideIndex);
            });
        });
        setInterval(nextSlide, 5000);

        // ---------- TYPEWRITER ----------
        const typedSpan = document.getElementById('typedText');
        const phrases = [
            'PSEB Affiliated School in Badrukhan.',
            'Nursery to 10th for Boys.',
            'Nursery to 12th for Girls.',
            'Open-air, green, and affordable.'
        ];
        let phraseIdx = 0,
            charIdx = 0,
            isDeleting = false;

        function typeEffect() {
            const current = phrases[phraseIdx];
            if (isDeleting) {
                typedSpan.textContent = current.substring(0, charIdx - 1);
                charIdx--;
            } else {
                typedSpan.textContent = current.substring(0, charIdx + 1);
                charIdx++;
            }
            if (!isDeleting && charIdx === current.length) {
                isDeleting = true;
                setTimeout(typeEffect, 2000);
                return;
            }
            if (isDeleting && charIdx === 0) {
                isDeleting = false;
                phraseIdx = (phraseIdx + 1) % phrases.length;
                setTimeout(typeEffect, 500);
                return;
            }
            setTimeout(typeEffect, isDeleting ? 35 : 70);
        }
        typeEffect();

        // ---------- STAT COUNTERS ----------
        const counters = [
            { el: document.getElementById('statYears'), target: 10, suffix: '+' },
            { el: document.getElementById('statStudents'), target: 380, suffix: '+' },
            { el: document.getElementById('statSatisfaction'), target: 180, suffix: '+' }
        ];
        let counted = false;

        function animateCounters() {
            if (counted) return;
            const rect = counters[0].el.closest('.stat-box').getBoundingClientRect();
            if (rect.top < window.innerHeight - 100) {
                counted = true;
                counters.forEach(c => {
                    let current = 0;
                    const step = Math.ceil(c.target / 55);
                    const interval = setInterval(() => {
                        current += step;
                        if (current >= c.target) {
                            c.el.textContent = c.target + c.suffix;
                            clearInterval(interval);
                        } else {
                            c.el.textContent = current + c.suffix;
                        }
                    }, 25);
                });
            }
        }
        window.addEventListener('scroll', animateCounters);
        setTimeout(animateCounters, 300);

        // ---------- STAGGERED ANIMATIONS (Observer) ----------
        const staggerElements = document.querySelectorAll('.stagger-children');
        const staggerObserver = new IntersectionObserver((entries) => {
            entries.forEach(entry => {
                if (entry.isIntersecting) {
                    entry.target.classList.add('visible');
                }
            });
        }, { threshold: 0.15 });
        staggerElements.forEach(el => staggerObserver.observe(el));

        // ---------- SCROLL FADE UP (Observer) ----------
        const fadeElements = document.querySelectorAll('.fade-up');
        const fadeObserver = new IntersectionObserver((entries) => {
            entries.forEach(entry => {
                if (entry.isIntersecting) {
                    entry.target.classList.add('visible');
                }
            });
        }, { threshold: 0.1 });
        fadeElements.forEach(el => fadeObserver.observe(el));

        // ---------- GALLERY LIGHTBOX ----------
        const lightbox = document.getElementById('lightbox');
        const lbImage = document.getElementById('lbImage');
        const closeLb = document.getElementById('closeLb');
        const prevLb = document.getElementById('prevLb');
        const nextLb = document.getElementById('nextLb');
        const galleryItems = document.querySelectorAll('.gallery-item');
        let currentImageIndex = 0;

        const images = [];
        galleryItems.forEach(item => {
            const style = window.getComputedStyle(item);
            const bg = style.backgroundImage;
            const match = bg.match(/url\(['"]?([^'"]+)['"]?\)/);
            if (match && match[1]) {
                images.push(match[1]);
            } else {
                images.push(
                'https://images.unsplash.com/photo-1580582932707-520aed937b7b?ixlib=rb-4.0.3&auto=format&fit=crop&w=800&q=80');
            }
        });

        function openLightbox(index) {
            currentImageIndex = index;
            lbImage.src = images[index] || images[0];
            lightbox.classList.add('active');
            document.body.style.overflow = 'hidden';
        }

        galleryItems.forEach((item, index) => {
            item.addEventListener('click', () => openLightbox(index));
        });

        closeLb.addEventListener('click', () => {
            lightbox.classList.remove('active');
            document.body.style.overflow = '';
        });

        lightbox.addEventListener('click', (e) => {
            if (e.target === lightbox) {
                lightbox.classList.remove('active');
                document.body.style.overflow = '';
            }
        });

        prevLb.addEventListener('click', () => {
            currentImageIndex = (currentImageIndex - 1 + images.length) % images.length;
            lbImage.src = images[currentImageIndex];
        });

        nextLb.addEventListener('click', () => {
            currentImageIndex = (currentImageIndex + 1) % images.length;
            lbImage.src = images[currentImageIndex];
        });

        document.addEventListener('keydown', (e) => {
            if (!lightbox.classList.contains('active')) return;
            if (e.key === 'Escape') { lightbox.classList.remove('active');
                document.body.style.overflow = ''; }
            if (e.key === 'ArrowLeft') prevLb.click();
            if (e.key === 'ArrowRight') nextLb.click();
        });

        // ---------- CONTACT FORM ----------
        document.getElementById('contactForm').addEventListener('submit', function(e) {
            e.preventDefault();
            alert('✅ Thank you! Your enquiry has been sent to Adarsh Public School, Badrukhan (PSEB 2170174). We will reach out shortly.');
            this.reset();
        });

        // ---------- HAMBURGER ----------
        const hamburger = document.getElementById('hamburger');
        const navLinks = document.getElementById('navLinks');
        hamburger.addEventListener('click', () => {
            hamburger.classList.toggle('active');
            navLinks.classList.toggle('active');
        });
        document.querySelectorAll('.nav-links a').forEach(link => {
            link.addEventListener('click', () => {
                hamburger.classList.remove('active');
                navLinks.classList.remove('active');
            });
        });

        // ---------- DYNAMIC YEAR ----------
        document.getElementById('year').textContent = new Date().getFullYear();

        console.log('🌿 Adarsh Public School - Badrukhan (Premium Edition) loaded!');
        console.log('🏫 Affiliation No: 2170174');
    </script>

</body>
</html>
