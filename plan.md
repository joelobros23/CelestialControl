# Project Plan: CelestialControl

**Description:** A simplified web hosting platform built on Ruby on Rails, offering basic domain management and user authentication.


## Development Goals

- [ ] Install and configure tailwindcss-rails: `bundle install`, `rails tailwindcss:install` and modify the `app/views/layouts/application.html.erb` to include the stylesheet link tag.
- [ ] Customize the Devise views to integrate Tailwind CSS styling for a consistent user experience. Override the Devise views using `rails generate devise:views`.
- [ ] Implement user associations for domains. Modify the Domain model to include `belongs_to :user`.  Modify the DomainsController's `create` and `update` actions to assign the domain to the current_user: `@domain = current_user.domains.build(domain_params)`.
- [ ] Add authorization to the DomainsController using `before_action :authenticate_user!` and `before_action :correct_user, only: [:edit, :update, :destroy]`. Implement the `correct_user` method to ensure a user can only manage their own domains.  Example: `def correct_user; @domain = current_user.domains.find_by(id: params[:id]); redirect_to root_url, notice: "Not authorized." if @domain.nil?; end`
- [ ] Implement basic domain status updates (e.g., 'active', 'inactive', 'pending') using a select box in the domain edit form. Style the domain index page to visually represent the status of each domain.
- [ ] Update the Domain model validations to include presence, uniqueness, and a valid domain name format using a custom validator or regex.
- [ ] Implement a simple pricing plan selection when creating a new domain. Provide a dropdown list with predefined plans.
- [ ] Customize the application layout and add a navigation bar using Tailwind CSS. Include links for sign in, sign up, sign out (if signed in), and a link to the user's domains.
- [ ] Secure the application by adding appropriate HTTP headers for security.  Consider using a gem like `secure_headers` or manually configure the headers.
- [ ] Add a simple dashboard to display the user's domains with associated data and metrics.
