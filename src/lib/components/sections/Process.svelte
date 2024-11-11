<script>
    import { inview } from 'svelte-inview';

    const processSteps = [
        {
            icon: 'fa-magnifying-glass',
            title: 'Discovery',
            description: 'We learn about your brand, goals, and target audience to create a tailored strategy.'
        },
        {
            icon: 'fa-chess',
            title: 'Strategy',
            description: 'Develop a comprehensive social media plan aligned with your business objectives.'
        },
        {
            icon: 'fa-pen-to-square',
            title: 'Creation',
            description: 'Produce engaging content that resonates with your audience and reflects your brand.'
        },
        {
            icon: 'fa-rocket',
            title: 'Growth',
            description: 'Monitor performance, engage with your audience, and optimize for better results.'
        }
    ];
</script>

<section class="process" use:inview={{ unobserveOnEnter: true }}>
    <div class="section-header">
        <h2>Our Process</h2>
        <div class="header-line"></div>
    </div>
    <div class="process-container">
        <div class="process-center-line"></div>
        <div class="process-steps">
            {#each processSteps as step, index}
                <div class="process-card {index % 2 === 0 ? 'left' : 'right'}" style="--delay: {index * 0.3}s">
                    <div class="step-content">
                        <div class="step-header">
                            <div class="step-icon-container">
                                <div class="step-icon-wrapper">
                                    <i class="fa-solid {step.icon}"></i>
                                    <div class="icon-ring"></div>
                                    <div class="icon-pulse"></div>
                                </div>
                                <div class="step-number">Step {index + 1}</div>
                            </div>
                        </div>
                        <div class="step-details">
                            <h3>{step.title}</h3>
                            <p>{step.description}</p>
                        </div>
                        <div class="step-connector">
                            <div class="connector-dot"></div>
                            <div class="connector-line">
                                <div class="line-progress"></div>
                            </div>
                        </div>
                    </div>
                </div>
            {/each}
        </div>
    </div>
</section>

<style>
    .process {
        padding: 4%;
        background-color: var(--text-color);
        position: relative;
        overflow: hidden;
    }

    .section-header {
        text-align: center;
        position: relative;
    }

    .section-header h2 {
        color: var(--services-text-color);
        font-size: 2.8rem;
        margin-bottom: 1rem;
        position: relative;
        display: inline-block;
    }

    .header-line {
        width: 80px;
        height: 4px;
        background: var(--background-color);
        margin: 1rem auto;
        border-radius: 2px;
        position: relative;
    }

    .process-container {
        max-width: 1200px;
        margin: 4rem auto 0;
        padding: 2rem;
        position: relative;
    }

    .process-center-line {
        position: absolute;
        left: 50%;
        top: 0;
        bottom: 0;
        width: 4px;
        background: linear-gradient(
            to bottom,
            transparent,
            var(--background-color) 10%,
            var(--background-color) 90%,
            transparent
        );
        opacity: 0.3;
        transform: translateX(-50%);
    }

    .process-steps {
        position: relative;
        display: flex;
        flex-direction: column;
        gap: 4rem;
    }

    .process-card {
        width: 42%;
        position: relative;
        animation: slideIn 0.8s ease forwards;
        animation-delay: var(--delay);
        opacity: 0;
    }

    .process-card.left {
        align-self: flex-start;
        transform: translateX(-30px);
    }

    .process-card.right {
        align-self: flex-end;
        transform: translateX(30px);
    }

    .step-content {
        background: white;
        padding: 2rem;
        border-radius: 1.5rem;
        box-shadow: 0 4px 20px rgba(0, 0, 0, 0.08);
        transition: all 0.4s cubic-bezier(0.165, 0.84, 0.44, 1);
        position: relative;
    }

    .step-icon-wrapper {
        position: relative;
        width: 60px;
        height: 60px;
        display: flex;
        align-items: center;
        justify-content: center;
        background: rgba(52, 179, 138, 0.1);
        border-radius: 50%;
        transition: all 0.4s ease;
    }

    .step-icon-wrapper i {
        font-size: 1.8rem;
        color: var(--background-color);
        position: relative;
        z-index: 2;
        transition: all 0.4s ease;
    }

    .icon-ring {
        position: absolute;
        top: 50%;
        left: 50%;
        transform: translate(-50%, -50%);
        width: 100%;
        height: 100%;
        border: 2px solid var(--background-color);
        border-radius: 50%;
        opacity: 0.2;
        transition: all 0.4s ease;
    }

    .icon-pulse {
        position: absolute;
        top: 50%;
        left: 50%;
        transform: translate(-50%, -50%);
        width: 100%;
        height: 100%;
        border-radius: 50%;
        background: var(--background-color);
        opacity: 0;
        animation: pulseCircle 2s infinite;
    }

    .step-details h3 {
        color: var(--services-text-color);
        font-size: 1.6rem;
        margin-bottom: 1rem;
    }

    .step-details p {
        color: var(--services-text-color);
        opacity: 0.8;
        line-height: 1.6;
    }

    .step-connector {
        position: absolute;
        top: 50%;
        width: 50px;
        height: 2px;
        display: flex;
        align-items: center;
    }

    .left .step-connector {
        right: -50px;
    }

    .right .step-connector {
        left: -50px;
    }

    .connector-dot {
        position: absolute;
        width: 12px;
        height: 12px;
        background: var(--background-color);
        border-radius: 50%;
        z-index: 2;
        transition: all 0.4s ease;
        top: 50%;
        transform: translateY(-50%);
    }

    .left .connector-dot {
        right: -10px;
    }

    .right .connector-dot {
        left: -10px;
    }

    .connector-line {
        position: relative;
        height: 3px;
        background: linear-gradient(
            to right,
            rgba(52, 179, 138, 0.2),
            rgba(52, 179, 138, 0.4)
        );
        width: 100%;
    }

    .step-number {
        font-weight: 700;
        color: var(--background-color);
        font-size: 1rem;
        letter-spacing: 0.5px;
        opacity: 0.8;
        transition: all 0.4s ease;
        margin-top: 0.5rem;
    }

    /* Animations */
    @keyframes slideIn {
        from {
            opacity: 0;
            transform: translateX(var(--slide-distance)) scale(0.95);
        }
        to {
            opacity: 1;
            transform: translateX(0) scale(1);
        }
    }

    @keyframes pulseCircle {
        0% {
            transform: translate(-50%, -50%) scale(0.95);
            opacity: 0.3;
        }
        50% {
            transform: translate(-50%, -50%) scale(1.2);
            opacity: 0;
        }
        100% {
            transform: translate(-50%, -50%) scale(0.95);
            opacity: 0.3;
        }
    }

    /* Hover effects */
    .step-content:hover {
        transform: translateY(-5px);
        box-shadow: 0 10px 30px rgba(0, 0, 0, 0.12);
    }

    .step-content:hover .step-icon-wrapper {
        transform: scale(1.1);
        background: rgba(52, 179, 138, 0.15);
    }

    .step-content:hover .step-number {
        transform: scale(1.1);
        opacity: 1;
    }

    /* Mobile responsive */
    @media (max-width: 768px) {
        .process-center-line {
            left: 30px;
        }

        .process-card {
            width: calc(100% - 60px);
            margin-left: 60px;
        }

        .process-card.left,
        .process-card.right {
            align-self: flex-start;
        }

        .step-connector {
            left: -50px !important;
            width: 50px !important;
        }

        .connector-dot {
            left: -56px !important;
        }

        .section-header h2 {
            font-size: 2.2rem;
        }
    }
</style> 