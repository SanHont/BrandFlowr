<script>
    import { inview } from 'svelte-inview';

    const testimonials = [
        {
            content: "BrandFlowr transformed our social media presence. Their creative approach and strategic thinking helped us connect with our audience in ways we never imagined. Our engagement rates have increased by 300% since working with them.",
            author: "Sarah Johnson",
            role: "Marketing Director",
            company: "TechStart Solutions",
            image: "https://ui-avatars.com/api/?name=Sarah+Johnson&background=34b38a&color=fff"
        },
        {
            content: "Professional, creative, and results-driven. The team at BrandFlowr consistently delivers content that engages our followers and drives real business results. They've helped us double our social media following in just 6 months.",
            author: "Michael van der Berg",
            role: "Business Owner",
            company: "Artisan Cafe Co.",
            image: "https://ui-avatars.com/api/?name=Michael+Berg&background=34b38a&color=fff"
        },
        {
            content: "Working with BrandFlowr has been a game-changer for our brand. Their attention to detail and understanding of our industry is exceptional. They've helped us build a strong community around our brand and increase our online sales.",
            author: "Emma Davis",
            role: "CEO",
            company: "Eco Lifestyle Brands",
            image: "https://ui-avatars.com/api/?name=Emma+Davis&background=34b38a&color=fff"
        }
    ];
</script>

<section class="testimonials" use:inview={{ unobserveOnEnter: true }}>
    <div class="section-header">
        <h2>What Our Clients Say</h2>
        <p class="section-subtext">Real feedback from businesses we've helped grow</p>
        <div class="header-line"></div>
    </div>
    <div class="testimonials-grid">
        {#each testimonials as testimonial, index}
            <div class="testimonial-card" style="--delay: {index * 0.2}s">
                <div class="testimonial-icon">
                    <i class="fa-solid fa-quote-left"></i>
                    <div class="icon-ring"></div>
                </div>
                <div class="rating">
                    {#each Array(5) as _}
                        <i class="fa-solid fa-star"></i>
                    {/each}
                </div>
                <p>{testimonial.content}</p>
                <div class="client-info">
                    <div class="client-profile">
                        <div class="client-image">
                            <img src={testimonial.image} alt={testimonial.author} />
                            <div class="client-status">
                                <i class="fa-solid fa-check"></i>
                            </div>
                        </div>
                        <div class="client-details">
                            <strong>{testimonial.author}</strong>
                            <span>{testimonial.role} at {testimonial.company}</span>
                        </div>
                    </div>
                </div>
            </div>
        {/each}
    </div>
</section>

<style>
    .testimonials {
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
        margin-bottom: 0.5rem;
    }

    .section-subtext {
        color: var(--text-color);
        font-size: 1.1rem;
        opacity: 0.9;
        margin-bottom: 1rem;
    }

    .header-line {
        width: 80px;
        height: 4px;
        background: var(--text-color);
        margin: 1rem auto;
        border-radius: 2px;
    }

    .testimonials-grid {
        display: grid;
        grid-template-columns: repeat(3, 1fr);
        gap: 2.5rem;
        max-width: 1200px;
        margin: 4rem auto 0;
        padding: 1rem;
    }

    .testimonial-card {
        background-color: var(--text-color);
        padding: 3rem 2rem 2rem;
        border-radius: 1.5rem;
        position: relative;
        box-shadow: 0 4px 20px rgba(0, 0, 0, 0.08);
        transition: all 0.4s cubic-bezier(0.165, 0.84, 0.44, 1);
        animation: fadeInUp 0.8s ease forwards;
        animation-delay: var(--delay);
        opacity: 0;
        display: flex;
        flex-direction: column;
        height: 100%;
    }

    .testimonial-icon {
        position: absolute;
        top: -30px;
        left: 50%;
        transform: translateX(-50%);
        width: 60px;
        height: 60px;
        background: var(--services-background-color);
        border-radius: 50%;
        display: flex;
        align-items: center;
        justify-content: center;
        box-shadow: 0 4px 15px rgba(0, 0, 0, 0.1);
    }

    .testimonial-icon i {
        font-size: 1.8rem;
        color: var(--text-color);
        position: relative;
        z-index: 2;
        transition: transform 0.3s ease;
    }

    .rating {
        color: #FFD700;
        margin-bottom: 1.5rem;
        font-size: 1.1rem;
        text-align: center;
    }

    .testimonial-card p {
        color: var(--services-text-color);
        font-size: 1.1rem;
        line-height: 1.7;
        margin-bottom: 2rem;
        position: relative;
        z-index: 1;
        flex-grow: 1;
        text-align: center;
        font-style: italic;
    }

    .client-info {
        border-top: 1px solid rgba(52, 179, 138, 0.1);
        margin-top: auto;
        padding-top: 1.5rem;
    }

    .client-profile {
        display: flex;
        align-items: center;
        gap: 1rem;
    }

    .client-image {
        position: relative;
    }

    .client-info img {
        width: 55px;
        height: 55px;
        border-radius: 1rem;
        border: 3px solid var(--services-background-color);
        transition: all 0.4s ease;
    }

    .client-status {
        position: absolute;
        bottom: -4px;
        right: -4px;
        width: 18px;
        height: 18px;
        background: var(--background-color);
        border: 2px solid white;
        border-radius: 50%;
        display: flex;
        align-items: center;
        justify-content: center;
    }

    .client-status i {
        color: white;
        font-size: 0.7rem;
    }

    .client-details {
        flex: 1;
    }

    .client-details strong {
        display: block;
        color: var(--services-text-color);
        font-size: 1.1rem;
        font-weight: 700;
        margin-bottom: 0.2rem;
    }

    .client-details span {
        display: block;
        color: var(--services-text-color);
        opacity: 0.7;
        font-size: 0.9rem;
    }

    /* Hover effects */
    .testimonial-card:hover {
        transform: translateY(-5px);
        box-shadow: 0 15px 35px rgba(0, 0, 0, 0.1);
    }

    .testimonial-card:hover img {
        transform: scale(1.05);
        border-color: var(--background-color);
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

    @media (max-width: 1200px) {
        .testimonials-grid {
            grid-template-columns: repeat(2, 1fr);
        }
    }

    @media (max-width: 768px) {
        .testimonials-grid {
            grid-template-columns: 1fr;
            max-width: 500px;
        }

        .section-header h2 {
            font-size: 2.2rem;
        }

        .testimonial-card {
            padding: 2.5rem 1.5rem 1.5rem;
        }
    }
</style> 