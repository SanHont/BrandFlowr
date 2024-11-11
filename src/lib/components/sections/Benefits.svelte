<script>
    import { inview } from 'svelte-inview';

    const benefits = [
        {
            icon: 'fa-bullseye',
            title: 'Strategic Approach',
            description: 'We create tailored social media strategies that align with your business goals and target audience.'
        },
        {
            icon: 'fa-lightbulb',
            title: 'Creative Excellence',
            description: 'Our team delivers unique, engaging content that makes your brand stand out in the digital space.'
        },
        {
            icon: 'fa-arrow-trend-up',
            title: 'Proven Results',
            description: 'Track your growth with detailed analytics and see real engagement improvements.'
        },
        {
            icon: 'fa-handshake',
            title: 'Personal Touch',
            description: 'We work closely with you to ensure your brands voice and values shine through in every post.'
        }
    ];
</script>

<section class="why-choose-us" use:inview={{ unobserveOnEnter: true }}>
    <div class="section-header">
        <h2>Why Choose BrandFlowr?</h2>
        <div class="header-line"></div>
    </div>
    <div class="benefits-grid">
        {#each benefits as benefit, index}
            <div class="benefit-card" style="--delay: {index * 0.15}s">
                <div class="benefit-icon-wrapper">
                    <i class="fa-solid {benefit.icon}"></i>
                    <div class="icon-ring"></div>
                </div>
                <div class="benefit-content">
                    <h3>{benefit.title}</h3>
                    <p>{benefit.description}</p>
                </div>
                <div class="card-background"></div>
            </div>
        {/each}
    </div>
</section>

<style>
    .why-choose-us {
        padding: 4%;
        background-color: var(--background-color);
        position: relative;
        overflow: hidden;
    }

    .section-header {
        text-align: center;
        position: relative;
    }

    .section-header h2 {
        color: var(--text-color);
        font-size: 2.8rem;
        margin-bottom: 1rem;
        position: relative;
        display: inline-block;
    }

    .header-line {
        width: 80px;
        height: 4px;
        background: var(--text-color);
        margin: 1rem auto;
        border-radius: 2px;
        position: relative;
    }

    .header-line::before,
    .header-line::after {
        content: '';
        position: absolute;
        width: 40px;
        height: 4px;
        background: var(--text-color);
        border-radius: 2px;
        opacity: 0.5;
    }

    .header-line::before {
        left: -50px;
    }

    .header-line::after {
        right: -50px;
    }

    .benefits-grid {
        display: grid;
        grid-template-columns: repeat(2, 1fr);
        gap: 2.5rem;
        max-width: 1200px;
        margin: 0 auto;
        padding: 1rem;
    }

    .benefit-card {
        background-color: var(--text-color);
        padding: 2.5rem;
        border-radius: 1.5rem;
        position: relative;
        transition: all 0.4s cubic-bezier(0.165, 0.84, 0.44, 1);
        overflow: hidden;
        animation: fadeInUp 0.6s ease forwards;
        animation-delay: var(--delay);
        opacity: 0;
        display: flex;
        gap: 1.5rem;
        align-items: flex-start;
    }

    .benefit-icon-wrapper {
        flex-shrink: 0;
        position: relative;
        width: 60px;
        height: 60px;
        margin: 0;
        display: flex;
        align-items: center;
        justify-content: center;
    }

    .benefit-icon-wrapper i {
        font-size: 1.8rem;
        color: var(--background-color);
        position: relative;
        z-index: 2;
        line-height: 1;
        transition: transform 0.3s ease;
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
        transition: all 0.3s ease;
    }

    .icon-ring::after {
        content: '';
        position: absolute;
        top: -8px;
        left: -8px;
        right: -8px;
        bottom: -8px;
        border: 2px solid var(--background-color);
        border-radius: 50%;
        opacity: 0.1;
        transition: all 0.3s ease;
    }

    .benefit-content {
        flex: 1;
        text-align: left;
    }

    .benefit-content h3 {
        color: var(--services-text-color);
        font-size: 1.5rem;
        margin-bottom: 0.8rem;
        font-weight: 700;
        transition: transform 0.3s ease;
    }

    .benefit-content p {
        color: var(--services-text-color);
        opacity: 0.8;
        line-height: 1.6;
        font-size: 1rem;
        transition: transform 0.3s ease;
    }

    .card-background {
        position: absolute;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        background: linear-gradient(
            135deg,
            rgba(52, 179, 138, 0.05) 0%,
            rgba(52, 179, 138, 0.02) 100%
        );
        opacity: 0;
        transition: opacity 0.3s ease;
        border-radius: 1.5rem;
    }

    /* Hover effects */
    .benefit-card:hover {
        transform: translateY(-5px);
        box-shadow: 0 10px 30px rgba(0, 0, 0, 0.1);
    }

    .benefit-card:hover .icon-ring {
        opacity: 0.4;
        transform: translate(-50%, -50%) rotate(45deg);
    }

    .benefit-card:hover .icon-ring::after {
        opacity: 0.2;
        transform: rotate(-45deg);
    }

    .benefit-card:hover .benefit-icon-wrapper i {
        transform: scale(1.1);
    }

    .benefit-card:hover .benefit-content h3 {
        transform: translateY(-2px);
    }

    .benefit-card:hover .benefit-content p {
        transform: translateY(-1px);
    }

    .benefit-card:hover .card-background {
        opacity: 1;
    }

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

    @media (max-width: 968px) {
        .benefits-grid {
            grid-template-columns: 1fr;
            max-width: 600px;
        }

        .benefit-card {
            padding: 2rem;
        }

        .section-header h2 {
            font-size: 2.2rem;
        }
    }
</style> 