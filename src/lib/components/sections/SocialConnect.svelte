<script>
    import { inview } from 'svelte-inview';

    const socialPlatforms = [
        {
            name: 'Instagram',
            icon: 'fa-brands fa-instagram',
            handle: '@brandflowr',
            link: 'https://instagram.com/brandflowr'
        },
        {
            name: 'LinkedIn',
            icon: 'fa-brands fa-linkedin-in',
            handle: 'BrandFlowr',
            link: 'https://linkedin.com/company/brandflowr'
        },
        {
            name: 'Facebook',
            icon: 'fa-brands fa-facebook',
            handle: 'BrandFlowr',
            link: 'https://facebook.com/brandflowr'
        }
    ];
</script>

<section class="social-connect" use:inview={{ unobserveOnEnter: true }}>
    <div class="connect-container">
        <div class="section-header">
            <span class="pre-title">Social Media</span>
            <h2>Follow Our Journey</h2>
            <p>Stay updated with our latest insights and success stories</p>
        </div>
        <div class="social-platforms">
            {#each socialPlatforms as platform, index}
                <a 
                    href={platform.link}
                    class="platform-card"
                    target="_blank"
                    rel="noopener noreferrer"
                    style="--delay: {index * 0.15}s"
                >
                    <div class="platform-content">
                        <i class="{platform.icon}"></i>
                        <span class="platform-handle">{platform.handle}</span>
                        <i class="fa-solid fa-arrow-right arrow-icon"></i>
                    </div>
                </a>
            {/each}
        </div>
    </div>
</section>

<style>
    .social-connect {
        padding: 4%;
        background-color: var(--brand-primary);
        position: relative;
        overflow: hidden;
    }

    .connect-container {
        max-width: 900px;
        margin: 0 auto;
    }

    .section-header {
        text-align: center;
        margin-bottom: 3rem;
    }

    .pre-title {
        display: block;
        color: var(--text-light);
        font-size: 0.9rem;
        text-transform: uppercase;
        letter-spacing: 3px;
        margin-bottom: 0.5rem;
        opacity: 0.8;
    }

    .section-header h2 {
        color: var(--text-light);
        font-size: 2.5rem;
        margin-bottom: 0.8rem;
    }

    .section-header p {
        color: var(--text-light);
        font-size: 1.1rem;
        opacity: 0.9;
        max-width: 500px;
        margin: 0 auto;
    }

    .social-platforms {
        display: flex;
        gap: 1.5rem;
        justify-content: center;
        padding: 1rem;
    }

    .platform-card {
        text-decoration: none;
        animation: fadeInUp 0.6s ease forwards;
        animation-delay: var(--delay);
        opacity: 0;
        flex: 1;
        max-width: 280px;
    }

    .platform-content {
        background: var(--text-light);
        padding: 1.5rem;
        border-radius: 1rem;
        transition: all 0.3s ease;
        display: flex;
        align-items: center;
        gap: 1rem;
    }

    .platform-content i:first-child {
        font-size: 1.5rem;
        color: var(--brand-primary);
    }

    .platform-handle {
        flex: 1;
        color: var(--text-primary);
        font-size: 1rem;
        font-weight: 500;
    }

    .arrow-icon {
        color: var(--text-muted);
        font-size: 0.9rem;
        transition: transform 0.3s ease;
    }

    /* Hover effects */
    .platform-content:hover {
        transform: translateY(-3px);
        box-shadow: var(--shadow-md);
    }

    .platform-content:hover .arrow-icon {
        transform: translateX(3px);
        color: var(--brand-primary);
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
        .social-platforms {
            flex-direction: column;
            align-items: center;
        }

        .platform-card {
            width: 100%;
            max-width: 300px;
        }

        .section-header h2 {
            font-size: 2rem;
        }

        .section-header p {
            font-size: 1rem;
        }
    }
</style> 