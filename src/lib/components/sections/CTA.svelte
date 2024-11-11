<script>
    import { inview } from 'svelte-inview';
</script>

<section class="cta-section" use:inview={{ unobserveOnEnter: true }}>
    <div class="cta-container">
        <div class="cta-content">
            <h2>Ready to Grow Your Brand?</h2>
            <p>Let's create a social media strategy that works for your business.</p>
            <div class="cta-buttons">
                <a href="/contact" class="cta-primary">
                    Schedule a Free Consultation
                    <i class="fa-solid fa-arrow-right"></i>
                </a>
                <a href="/portfolio" class="cta-secondary">
                    View Our Work
                    <i class="fa-solid fa-images"></i>
                </a>
            </div>
        </div>
        <div class="cta-background">
            <div class="background-shapes">
                <div class="shape shape-1"></div>
                <div class="shape shape-2"></div>
                <div class="shape shape-3"></div>
            </div>
        </div>
    </div>
</section>

<style>
    .cta-section {
        padding: 4%;
        background-color: var(--text-color);
        position: relative;
        overflow: hidden;
    }

    .cta-container {
        max-width: 1200px;
        margin: 0 auto;
        position: relative;
        z-index: 1;
    }

    .cta-content {
        text-align: center;
        position: relative;
        z-index: 2;
        animation: fadeInUp 0.8s ease forwards;
        opacity: 0;
    }

    .cta-content h2 {
        color: var(--services-text-color);
        font-size: 3.5rem;
        margin-bottom: 1.5rem;
        font-weight: 800;
    }

    .cta-content p {
        color: var(--services-text-color);
        font-size: 1.3rem;
        margin-bottom: 3rem;
        opacity: 0.9;
    }

    .cta-buttons {
        display: flex;
        gap: 2rem;
        justify-content: center;
    }

    .cta-primary,
    .cta-secondary {
        padding: 1.2rem 2.5rem;
        border-radius: 3rem;
        font-weight: 600;
        text-decoration: none;
        transition: all 0.4s cubic-bezier(0.165, 0.84, 0.44, 1);
        display: flex;
        align-items: center;
        gap: 1rem;
    }

    .cta-primary {
        background-color: var(--background-color);
        color: var(--text-color);
        box-shadow: 0 4px 15px rgba(52, 179, 138, 0.3);
    }

    .cta-secondary {
        background-color: transparent;
        color: var(--services-text-color);
        border: 2px solid var(--background-color);
    }

    .cta-background {
        position: absolute;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        z-index: 1;
    }

    .background-shapes {
        position: absolute;
        width: 100%;
        height: 100%;
    }

    .shape {
        position: absolute;
        background: var(--background-color);
        border-radius: 50%;
        opacity: 0.05;
    }

    .shape-1 {
        width: 300px;
        height: 300px;
        top: -150px;
        right: -100px;
        animation: float 8s infinite ease-in-out;
    }

    .shape-2 {
        width: 200px;
        height: 200px;
        bottom: -100px;
        left: -50px;
        animation: float 8s infinite ease-in-out reverse;
    }

    .shape-3 {
        width: 150px;
        height: 150px;
        top: 50%;
        left: 50%;
        transform: translate(-50%, -50%);
        animation: pulse 6s infinite ease-in-out;
    }

    /* Hover effects */
    .cta-primary:hover {
        transform: translateY(-3px);
        box-shadow: 0 8px 25px rgba(52, 179, 138, 0.4);
        background-color: #2a9c76;
    }

    .cta-secondary:hover {
        transform: translateY(-3px);
        box-shadow: 0 8px 25px rgba(0, 0, 0, 0.1);
        background-color: rgba(52, 179, 138, 0.1);
    }

    .cta-primary:hover i {
        transform: translateX(5px);
    }

    .cta-secondary:hover i {
        transform: scale(1.1);
    }

    /* Animations */
    @keyframes fadeInUp {
        from {
            opacity: 0;
            transform: translateY(20px);
        }
        to {
            opacity: 1;
            transform: translateY(0);
        }
    }

    @keyframes float {
        0%, 100% {
            transform: translateY(0);
        }
        50% {
            transform: translateY(20px);
        }
    }

    @keyframes pulse {
        0%, 100% {
            transform: translate(-50%, -50%) scale(1);
            opacity: 0.05;
        }
        50% {
            transform: translate(-50%, -50%) scale(1.2);
            opacity: 0.02;
        }
    }

    /* Mobile responsive */
    @media (max-width: 768px) {
        .cta-section {
            padding: 6rem 5%;
        }

        .cta-content h2 {
            font-size: 2.5rem;
        }

        .cta-content p {
            font-size: 1.1rem;
        }

        .cta-buttons {
            flex-direction: column;
            gap: 1rem;
        }

        .cta-primary,
        .cta-secondary {
            width: 100%;
            justify-content: center;
        }

        .shape {
            display: none;
        }
    }
</style> 