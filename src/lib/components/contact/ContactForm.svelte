<script>
    let isSubmitting = false;
    let showSuccess = false;

    async function handleSubmit(event) {
        event.preventDefault();
        isSubmitting = true;
        const form = event.target;
        const formData = new FormData(form);

        try {
            const response = await fetch('https://api.web3forms.com/submit', {
                method: 'POST',
                body: formData
            });

            const data = await response.json();

            if (data.success) {
                showSuccess = true;
                form.reset();
                setTimeout(() => {
                    showSuccess = false;
                }, 5000);
            }
        } catch (error) {
            console.error('Error submitting form:', error);
        } finally {
            isSubmitting = false;
        }
    }
</script>

<section class="contact-form">
    <h2>Get in Touch</h2>
    <p class="form-description">
        Fill out the form below and we'll get back to you within 24 hours.
    </p>

    <form
        action="https://api.web3forms.com/submit"
        method="POST"
        class="form-content"
        on:submit={handleSubmit}
    >
        <input type="hidden" name="access_key" value="644ce989-a3d6-447c-b582-30bba4a30d31" />
        <input type="hidden" name="subject" value="New Contact Form Submission - BrandFlowr" />
        <input type="hidden" name="from_name" value="BrandFlowr Contact" />
        <input type="checkbox" name="botcheck" class="hidden" style="display: none;" />

        <div class="form-group">
            <label for="name">Full Name *</label>
            <input type="text" id="name" name="name" required placeholder="John Doe" />
        </div>

        <div class="form-row">
            <div class="form-group">
                <label for="email">Email Address *</label>
                <input type="email" id="email" name="email" required placeholder="john@company.com" />
            </div>
            <div class="form-group">
                <label for="phone">Phone Number</label>
                <input type="tel" id="phone" name="phone" placeholder="+31 6 1234 5678" />
            </div>
        </div>

        <div class="form-group">
            <label for="company">Company Name</label>
            <input type="text" id="company" name="company" placeholder="Your Company Ltd." />
        </div>

        <div class="form-group">
            <label for="service">Service Interest *</label>
            <select id="service" name="service" required>
                <option value="">Select a service...</option>
                <option value="social-management">Social Media Management</option>
                <option value="content-creation">Content Creation</option>
                <option value="strategy">Strategy & Consulting</option>
                <option value="other">Other</option>
            </select>
        </div>

        <div class="form-group">
            <label for="message">Your Message *</label>
            <textarea
                id="message"
                name="message"
                rows="5"
                required
                placeholder="Tell us about your project and goals..."
            ></textarea>
        </div>

        <div class="form-group">
            <label class="checkbox-container">
                <input type="checkbox" name="privacy" required />
                <span class="checkmark"></span>
                I agree to the privacy policy and terms of service
            </label>
        </div>

        {#if showSuccess}
            <div class="success-message" role="alert">
                <i class="fa-solid fa-check-circle"></i>
                <div class="success-content">
                    <h4>Message Sent Successfully!</h4>
                    <p>We'll get back to you within 24 hours.</p>
                </div>
            </div>
        {/if}

        <button type="submit" class="submit-btn" disabled={isSubmitting}>
            {#if isSubmitting}
                <div class="loading-spinner"></div>
                Sending...
            {:else}
                Send Message
                <i class="fa-solid fa-paper-plane"></i>
            {/if}
        </button>
    </form>
</section>

<style>
    .contact-form {
        min-height: 500px;
        height: 100%;
        background: var(--bg-primary);
        padding: 2rem;
        border-radius: 1rem;
    }

    h2 {
        font-family: 'Montserrat', sans-serif;
        font-weight: 700;
        color: var(--text-primary);
        font-size: 1.8rem;
        margin-bottom: 1rem;
    }

    .form-description {
        font-family: 'Montserrat', sans-serif;
        font-weight: 400;
        color: var(--text-muted);
        font-size: 1.1rem;
        margin-top: 0.5rem;
    }

    .form-content {
        margin-top: 2rem;
        display: flex;
        flex-direction: column;
        gap: 1.5rem;
    }

    .form-row {
        display: grid;
        grid-template-columns: 1fr 1fr;
        gap: 1.5rem;
    }

    .form-group {
        display: flex;
        flex-direction: column;
        gap: 0.5rem;
    }

    label {
        font-family: 'Montserrat', sans-serif;
        font-weight: 600;
        color: var(--text-primary);
        font-size: 0.95rem;
    }

    input,
    select,
    textarea {
        font-family: 'Montserrat', sans-serif;
        font-weight: 400;
        padding: 1rem;
        border: 2px solid rgba(52, 179, 138, 0.1);
        border-radius: 0.8rem;
        font-size: 1rem;
        transition: all 0.3s ease;
        background-color: white;
    }

    input::placeholder,
    textarea::placeholder {
        font-family: 'Montserrat', sans-serif;
        font-weight: 400;
        color: var(--text-muted);
        opacity: 0.7;
    }

    input:focus,
    select:focus,
    textarea:focus {
        outline: none;
        border-color: var(--brand-primary);
        box-shadow: 0 0 0 4px rgba(52, 179, 138, 0.1);
    }

    .checkbox-container {
        font-family: 'Montserrat', sans-serif;
        font-weight: 400;
        display: flex;
        align-items: center;
        gap: 0.5rem;
        font-size: 0.9rem;
        color: var(--text-muted);
        cursor: pointer;
    }

    .submit-btn {
        font-family: 'Montserrat', sans-serif;
        font-weight: 600;
        background: var(--brand-primary);
        color: var(--text-light);
        padding: 1.2rem 2rem;
        border: none;
        border-radius: 0.8rem;
        font-size: 1rem;
        cursor: pointer;
        transition: all 0.3s ease;
        display: flex;
        align-items: center;
        justify-content: center;
        gap: 0.8rem;
        margin-top: 1rem;
    }

    .submit-btn:hover {
        background: var(--brand-primary-dark);
        transform: translateY(-2px);
    }

    .submit-btn i {
        font-size: 1.1rem;
        transition: transform 0.3s ease;
    }

    .submit-btn:hover i {
        transform: translateX(3px);
    }

    select {
        appearance: none;
        -webkit-appearance: none;
        -moz-appearance: none;
        background-image: url("data:image/svg+xml;charset=UTF-8,%3csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 24 24' fill='none' stroke='%2334b38a' stroke-width='2' stroke-linecap='round' stroke-linejoin='round'%3e%3cpolyline points='6 9 12 15 18 9'%3e%3c/polyline%3e%3c/svg%3e");
        background-repeat: no-repeat;
        background-position: right 1rem center;
        background-size: 1.2em;
        padding-right: 3rem;
        cursor: pointer;
    }

    select::-ms-expand {
        display: none;
    }

    select option {
        font-family: 'Montserrat', sans-serif;
        font-weight: 400;
        color: var(--text-primary);
        padding: 1rem;
        background-color: white;
    }

    select:hover {
        border-color: var(--brand-primary);
        background-color: rgba(52, 179, 138, 0.02);
    }

    select:focus {
        outline: none;
        border-color: var(--brand-primary);
        box-shadow: 0 0 0 4px rgba(52, 179, 138, 0.1);
        background-color: white;
    }

    select:disabled {
        background-color: #f5f5f5;
        cursor: not-allowed;
        opacity: 0.7;
    }

    select option:checked {
        background-color: var(--brand-primary);
        color: white;
    }

    select option:hover {
        background-color: rgba(52, 179, 138, 0.1);
    }

    .success-message {
        background-color: rgba(52, 179, 138, 0.1);
        border: 2px solid var(--brand-primary);
        border-radius: 0.8rem;
        padding: 1rem;
        display: flex;
        align-items: center;
        gap: 1rem;
        animation: slideIn 0.3s ease;
    }

    .success-message i {
        color: var(--brand-primary);
        font-size: 1.5rem;
    }

    .success-content h4 {
        color: var(--brand-primary);
        font-size: 1.1rem;
        margin-bottom: 0.2rem;
    }

    .success-content p {
        color: var(--text-muted);
        font-size: 0.9rem;
    }

    .loading-spinner {
        width: 20px;
        height: 20px;
        border: 2px solid var(--text-light);
        border-top-color: transparent;
        border-radius: 50%;
        animation: spin 0.8s linear infinite;
    }

    .submit-btn:disabled {
        opacity: 0.7;
        cursor: not-allowed;
    }

    @keyframes spin {
        to { transform: rotate(360deg); }
    }

    @keyframes slideIn {
        from {
            opacity: 0;
            transform: translateY(-10px);
        }
        to {
            opacity: 1;
            transform: translateY(0);
        }
    }

    @media (max-width: 768px) {
        .form-row {
            grid-template-columns: 1fr;
        }
    }
</style> 