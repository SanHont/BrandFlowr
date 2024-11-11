<script>
    import { inview } from 'svelte-inview';

    const services = [
        {
            icon: 'fa-mobile-screen-button',
            title: 'Social Media Management',
            description: 'Full-service management of your social media presence across all major platforms.',
            color: '#34b38a'
        },
        {
            icon: 'fa-camera',
            title: 'Content Creation',
            description: 'Eye-catching visuals and engaging copy that resonates with your audience.',
            color: '#4ecca3'
        },
        {
            icon: 'fa-chart-line',
            title: 'Strategy & Analytics',
            description: 'Data-driven strategies to grow your online presence and engage your audience.',
            color: '#76d7b8'
        }
    ];
</script>

<section class="featured-services" use:inview={{ unobserveOnEnter: true }}>
    <h2>Our Services</h2>
    <div class="services-grid">
        {#each services as service, index}
            <div class="service-card" style="--delay: {index * 0.2}s; --accent-color: {service.color}">
                <div class="service-icon">
                    <i class="fa-solid {service.icon}"></i>
                    <div class="icon-background"></div>
                </div>
                <h3>{service.title}</h3>
                <p>{service.description}</p>
                <div class="service-hover">
                    <span class="learn-more">Learn More →</span>
                </div>
            </div>
        {/each}
    </div>
</section>

<style>
    .featured-services {
        padding: 4%;
        background-color: var(--text-color);
        position: relative;
        overflow: hidden;
    }

    .featured-services h2 {
        text-align: center;
        color: var(--services-text-color);
        margin-bottom: 4rem;
        font-size: 2.8rem;
        position: relative;
        display: inline-block;
        left: 50%;
        transform: translateX(-50%);
    }

    .featured-services h2::after {
        content: '';
        position: absolute;
        bottom: -10px;
        left: 50%;
        transform: translateX(-50%);
        width: 50%;
        height: 3px;
        background: var(--background-color);
        border-radius: 2px;
    }

    .services-grid {
        display: grid;
        grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
        gap: 2.5rem;
        max-width: 1200px;
        margin: 0 auto;
        padding: 1rem;
    }

    .service-card {
        background-color: white;
        padding: 2.5rem;
        border-radius: 1.5rem;
        text-align: center;
        position: relative;
        transition: all 0.4s cubic-bezier(0.165, 0.84, 0.44, 1);
        box-shadow: 0 4px 20px rgba(0, 0, 0, 0.05);
        animation: fadeInUp 0.6s ease forwards;
        animation-delay: var(--delay);
        opacity: 0;
        cursor: pointer;
    }

    .service-icon {
        position: relative;
        width: 80px;
        height: 80px;
        margin: 0 auto 1.5rem;
    }

    .service-icon i {
        font-size: 2.2rem;
        color: var(--accent-color);
        position: relative;
        z-index: 2;
        line-height: 80px;
    }

    .icon-background {
        position: absolute;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        background-color: var(--accent-color);
        opacity: 0.1;
        border-radius: 1rem;
        transform: rotate(45deg);
        transition: all 0.3s ease;
    }

    .service-card h3 {
        color: var(--services-text-color);
        margin-bottom: 1rem;
        font-size: 1.6rem;
        font-weight: 700;
        transition: color 0.3s ease;
    }

    .service-card p {
        color: var(--services-text-color);
        opacity: 0.8;
        line-height: 1.7;
        margin-bottom: 1.5rem;
        transition: opacity 0.3s ease;
    }

    .service-hover {
        position: absolute;
        bottom: 0;
        left: 0;
        width: 100%;
        padding: 1.5rem;
        background: linear-gradient(
            to top,
            rgba(255, 255, 255, 1) 0%,
            rgba(255, 255, 255, 0) 100%
        );
        opacity: 0;
        transition: all 0.3s ease;
    }

    .learn-more {
        color: var(--accent-color);
        font-weight: 600;
        font-size: 1.1rem;
    }

    /* Hover effects */
    .service-card:hover {
        transform: translateY(-10px);
        box-shadow: 0 10px 30px rgba(0, 0, 0, 0.1);
    }

    .service-card:hover .icon-background {
        transform: rotate(90deg) scale(1.1);
        opacity: 0.15;
    }

    .service-card:hover .service-hover {
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

    @media (max-width: 768px) {
        .services-grid {
            grid-template-columns: 1fr;
            padding: 0.5rem;
        }

        .service-card {
            padding: 2rem;
        }

        .featured-services h2 {
            font-size: 2.2rem;
        }
    }
</style> 