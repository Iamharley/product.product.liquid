# product.product.liquid
<!-- 
Template: Page Produit TRUFF-Style pour HarleyVape.love
Inspiration: Design TRUFF avec couleurs Harley Route 66
Layout: 2 colonnes responsive, galerie images + infos produit
-->

<style>
  /* === PAGE PRODUIT TRUFF-STYLE === */
  .hv-product-page {
    background: var(--hv-creme-claire);
    padding: var(--hv-space-2xl) 0;
    min-height: 80vh;
  }

  .hv-product-container {
    max-width: 1200px;
    margin: 0 auto;
    padding: 0 var(--hv-space-lg);
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: var(--hv-space-3xl);
    align-items: start;
  }

  /* === GALERIE IMAGES (GAUCHE) === */
  .hv-product-gallery {
    position: sticky;
    top: 120px;
  }

  .hv-main-image {
    position: relative;
    margin-bottom: var(--hv-space-lg);
    border-radius: var(--hv-radius-xl);
    overflow: hidden;
    background: white;
    box-shadow: var(--hv-shadow-medium);
    border: 2px solid var(--hv-beige-dore);
  }

  .hv-main-image img {
    width: 100%;
    height: 500px;
    object-fit: cover;
    transition: var(--hv-transition-smooth);
  }

  .hv-main-image:hover img {
    transform: scale(1.05);
  }

  .hv-badge-container {
    position: absolute;
    top: var(--hv-space-lg);
    left: var(--hv-space-lg);
    display: flex;
    flex-direction: column;
    gap: var(--hv-space-sm);
  }

  .hv-badge {
    background: var(--hv-gradient-sunset);
    color: white;
    padding: 6px 12px;
    border-radius: 20px;
    font-size: 0.85rem;
    font-weight: var(--hv-font-weight-bold);
    box-shadow: var(--hv-shadow-soft);
    text-align: center;
  }

  .hv-badge.new {
    background: linear-gradient(135deg, #10B981 0%, #059669 100%);
  }

  .hv-badge.sale {
    background: linear-gradient(135deg, #EF4444 0%, #DC2626 100%);
  }

  /* === THUMBNAILS === */
  .hv-thumbnails {
    display: flex;
    gap: var(--hv-space-md);
    overflow-x: auto;
    padding: var(--hv-space-sm) 0;
  }

  .hv-thumbnail {
    flex-shrink: 0;
    width: 80px;
    height: 80px;
    border-radius: var(--hv-radius-md);
    overflow: hidden;
    border: 2px solid var(--hv-beige-dore);
    cursor: pointer;
    transition: var(--hv-transition-fast);
  }

  .hv-thumbnail:hover,
  .hv-thumbnail.active {
    border-color: var(--hv-orange-punchy);
    transform: scale(1.05);
  }

  .hv-thumbnail img {
    width: 100%;
    height: 100%;
    object-fit: cover;
  }

  /* === INFORMATIONS PRODUIT (DROITE) === */
  .hv-product-info {
    padding: var(--hv-space-lg) 0;
  }

  .hv-product-header {
    margin-bottom: var(--hv-space-xl);
  }

  .hv-product-vendor {
    color: var(--hv-orange-punchy);
    font-size: 0.9rem;
    font-weight: var(--hv-font-weight-medium);
    text-transform: uppercase;
    letter-spacing: 1px;
    margin-bottom: var(--hv-space-sm);
  }

  .hv-product-title {
    font-size: clamp(1.8rem, 4vw, 2.5rem);
    font-weight: var(--hv-font-weight-bold);
    color: var(--hv-marron-doux);
    line-height: 1.2;
    margin-bottom: var(--hv-space-md);
  }

  .hv-product-rating {
    display: flex;
    align-items: center;
    gap: var(--hv-space-sm);
    margin-bottom: var(--hv-space-lg);
  }

  .hv-stars {
    display: flex;
    gap: 2px;
  }

  .hv-star {
    width: 18px;
    height: 18px;
    color: var(--hv-orange-punchy);
  }

  .hv-rating-text {
    color: var(--hv-marron-doux);
    font-size: 0.9rem;
    opacity: 0.8;
  }

  /* === PRIX === */
  .hv-price-section {
    margin-bottom: var(--hv-space-xl);
    padding: var(--hv-space-lg);
    background: white;
    border-radius: var(--hv-radius-lg);
    border: 2px solid var(--hv-beige-dore);
    box-shadow: var(--hv-shadow-soft);
  }

  .hv-price-container {
    display: flex;
    align-items: baseline;
    gap: var(--hv-space-md);
    margin-bottom: var(--hv-space-md);
  }

  .hv-price-current {
    font-size: 2rem;
    font-weight: var(--hv-font-weight-bold);
    color: var(--hv-orange-punchy);
  }

  .hv-price-compare {
    font-size: 1.2rem;
    color: var(--hv-marron-doux);
    opacity: 0.6;
    text-decoration: line-through;
  }

  .hv-savings {
    background: var(--hv-gradient-sunset);
    color: white;
    padding: 4px 12px;
    border-radius: 16px;
    font-size: 0.85rem;
    font-weight: var(--hv-font-weight-bold);
  }

  /* === QUANTITÉ ET VARIANTS === */
  .hv-variant-section {
    margin-bottom: var(--hv-space-xl);
  }

  .hv-variant-title {
    font-weight: var(--hv-font-weight-bold);
    color: var(--hv-marron-doux);
    margin-bottom: var(--hv-space-md);
    font-size: 1.1rem;
  }

  .hv-quantity-container {
    display: flex;
    align-items: center;
    gap: var(--hv-space-lg);
    margin-bottom: var(--hv-space-lg);
  }

  .hv-quantity-label {
    font-weight: var(--hv-font-weight-medium);
    color: var(--hv-marron-doux);
  }

  .hv-quantity-selector {
    display: flex;
    align-items: center;
    border: 2px solid var(--hv-beige-dore);
    border-radius: var(--hv-radius-md);
    overflow: hidden;
    background: white;
  }

  .hv-qty-btn {
    width: 40px;
    height: 40px;
    background: transparent;
    border: none;
    display: flex;
    align-items: center;
    justify-content: center;
    cursor: pointer;
    color: var(--hv-marron-doux);
    font-weight: var(--hv-font-weight-bold);
    transition: var(--hv-transition-fast);
  }

  .hv-qty-btn:hover {
    background: var(--hv-beige-medium);
    color: var(--hv-orange-punchy);
  }

  .hv-qty-input {
    width: 60px;
    height: 40px;
    border: none;
    text-align: center;
    font-weight: var(--hv-font-weight-medium);
    color: var(--hv-marron-doux);
    background: transparent;
  }

  .hv-qty-input:focus {
    outline: none;
  }

  /* === VARIANTES COULEUR/SAVEUR === */
  .hv-variant-options {
    display: flex;
    flex-wrap: wrap;
    gap: var(--hv-space-sm);
    margin-bottom: var(--hv-space-lg);
  }

  .hv-variant-option {
    padding: var(--hv-space-sm) var(--hv-space-md);
    border: 2px solid var(--hv-beige-dore);
    border-radius: var(--hv-radius-md);
    background: white;
    color: var(--hv-marron-doux);
    cursor: pointer;
    transition: var(--hv-transition-fast);
    font-weight: var(--hv-font-weight-medium);
  }

  .hv-variant-option:hover,
  .hv-variant-option.selected {
    border-color: var(--hv-orange-punchy);
    background: var(--hv-orange-punchy);
    color: white;
    transform: translateY(-2px);
  }

  /* === BOUTONS CTA === */
  .hv-cta-section {
    margin-bottom: var(--hv-space-xl);
  }

  .hv-add-to-cart {
    width: 100%;
    background: var(--hv-gradient-sunset);
    color: white;
    border: none;
    border-radius: var(--hv-radius-lg);
    padding: var(--hv-space-lg) var(--hv-space-xl);
    font-size: 1.1rem;
    font-weight: var(--hv-font-weight-bold);
    cursor: pointer;
    transition: var(--hv-transition-smooth);
    position: relative;
    overflow: hidden;
    margin-bottom: var(--hv-space-md);
    min-height: 56px;
    display: flex;
    align-items: center;
    justify-content: center;
    gap: var(--hv-space-sm);
  }

  .hv-add-to-cart::before {
    content: '';
    position: absolute;
    top: 0;
    left: -100%;
    width: 100%;
    height: 100%;
    background: linear-gradient(90deg, transparent, rgba(255, 255, 255, 0.2), transparent);
    transition: var(--hv-transition-smooth);
  }

  .hv-add-to-cart:hover {
    transform: translateY(-3px);
    box-shadow: var(--hv-shadow-strong);
  }

  .hv-add-to-cart:hover::before {
    left: 100%;
  }

  .hv-buy-now {
    width: 100%;
    background: transparent;
    color: var(--hv-orange-punchy);
    border: 2px solid var(--hv-orange-punchy);
    border-radius: var(--hv-radius-lg);
    padding: var(--hv-space-md) var(--hv-space-xl);
    font-size: 1rem;
    font-weight: var(--hv-font-weight-bold);
    cursor: pointer;
    transition: var(--hv-transition-smooth);
    min-height: 48px;
  }

  .hv-buy-now:hover {
    background: var(--hv-orange-punchy);
    color: white;
    transform: translateY(-2px);
    box-shadow: var(--hv-shadow-medium);
  }

  /* === DESCRIPTION PRODUIT === */
  .hv-product-description {
    margin-bottom: var(--hv-space-xl);
    padding: var(--hv-space-xl);
    background: white;
    border-radius: var(--hv-radius-lg);
    border: 2px solid var(--hv-beige-dore);
    box-shadow: var(--hv-shadow-soft);
  }

  .hv-description-title {
    font-size: 1.3rem;
    font-weight: var(--hv-font-weight-bold);
    color: var(--hv-marron-doux);
    margin-bottom: var(--hv-space-md);
  }

  .hv-description-content {
    color: var(--hv-marron-doux);
    line-height: 1.7;
    font-size: 1rem;
  }

  .hv-description-content p {
    margin-bottom: var(--hv-space-md);
  }

  .hv-description-content ul {
    margin: var(--hv-space-md) 0;
    padding-left: var(--hv-space-lg);
  }

  .hv-description-content li {
    margin-bottom: var(--hv-space-sm);
  }

  /* === INFORMATIONS TECHNIQUES === */
  .hv-product-specs {
    background: var(--hv-beige-medium);
    border-radius: var(--hv-radius-lg);
    padding: var(--hv-space-xl);
    border: 2px solid var(--hv-beige-dore);
  }

  .hv-specs-title {
    font-size: 1.2rem;
    font-weight: var(--hv-font-weight-bold);
    color: var(--hv-marron-doux);
    margin-bottom: var(--hv-space-lg);
  }

  .hv-specs-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: var(--hv-space-md);
  }

  .hv-spec-item {
    display: flex;
    justify-content: space-between;
    padding: var(--hv-space-sm) 0;
    border-bottom: 1px solid var(--hv-beige-dore);
  }

  .hv-spec-label {
    font-weight: var(--hv-font-weight-medium);
    color: var(--hv-marron-doux);
  }

  .hv-spec-value {
    color: var(--hv-orange-punchy);
    font-weight: var(--hv-font-weight-medium);
  }

  /* === RESPONSIVE === */
  @media (max-width: 968px) {
    .hv-product-container {
      grid-template-columns: 1fr;
      gap: var(--hv-space-xl);
    }
    
    .hv-product-gallery {
      position: static;
      order: 1;
    }
    
    .hv-product-info {
      order: 2;
    }
    
    .hv-main-image img {
      height: 400px;
    }
    
    .hv-specs-grid {
      grid-template-columns: 1fr;
    }
  }

  @media (max-width: 768px) {
    .hv-product-page {
      padding: var(--hv-space-xl) 0;
    }
    
    .hv-main-image img {
      height: 320px;
    }
    
    .hv-quantity-container {
      flex-direction: column;
      align-items: stretch;
      gap: var(--hv-space-md);
    }
    
    .hv-variant-options {
      justify-content: center;
    }
  }

  @media (max-width: 480px) {
    .hv-price-container {
      flex-direction: column;
      align-items: flex-start;
      gap: var(--hv-space-sm);
    }
    
    .hv-thumbnails {
      justify-content: center;
    }
  }
</style>

<div class="hv-product-page">
  <div class="hv-product-container">
    
    <!-- Galerie Images (Gauche) -->
    <div class="hv-product-gallery">
      <div class="hv-main-image">
        {% if product.featured_image %}
          <img id="main-product-image" 
               src="{{ product.featured_image | img_url: '800x800' }}" 
               alt="{{ product.featured_image.alt | escape }}"
               loading="eager">
        {% else %}
          <div style="height: 500px; background: var(--hv-gray-warm); display: flex; align-items: center; justify-content: center; color: var(--hv-marron-doux);">
            <span>Image à venir</span>
          </div>
        {% endif %}
        
        <!-- Badges -->
        <div class="hv-badge-container">
          {% if product.tags contains 'nouveau' %}
            <span class="hv-badge new">Nouveau</span>
          {% endif %}
          {% if product.compare_at_price > product.price %}
            <span class="hv-badge sale">Promo</span>
          {% endif %}
          {% if product.tags contains 'populaire' %}
            <span class="hv-badge">Populaire</span>
          {% endif %}
        </div>
      </div>
      
      <!-- Thumbnails -->
      {% if product.images.size > 1 %}
        <div class="hv-thumbnails">
          {% for image in product.images %}
            <div class="hv-thumbnail {% if forloop.first %}active{% endif %}" 
                 onclick="changeMainImage('{{ image | img_url: '800x800' }}', this)">
              <img src="{{ image | img_url: '100x100' }}" 
                   alt="{{ image.alt | escape }}"
                   loading="lazy">
            </div>
          {% endfor %}
        </div>
      {% endif %}
    </div>

    <!-- Informations Produit (Droite) -->
    <div class="hv-product-info">
      
      <!-- Header Produit -->
      <div class="hv-product-header">
        {% if product.vendor != blank %}
          <div class="hv-product-vendor">{{ product.vendor }}</div>
        {% endif %}
        
        <h1 class="hv-product-title">{{ product.title }}</h1>
        
        <!-- Rating fictif pour demo -->
        <div class="hv-product-rating">
          <div class="hv-stars">
            {% for i in (1..5) %}
              <svg class="hv-star" fill="currentColor" viewBox="0 0 20 20">
                <path d="M9.049 2.927c.3-.921 1.603-.921 1.902 0l1.07 3.292a1 1 0 00.95.69h3.462c.969 0 1.371 1.24.588 1.81l-2.8 2.034a1 1 0 00-.364 1.118l1.07 3.292c.3.921-.755 1.688-1.54 1.118l-2.8-2.034a1 1 0 00-1.175 0l-2.8 2.034c-.784.57-1.838-.197-1.539-1.118l1.07-3.292a1 1 0 00-.364-1.118L2.98 8.72c-.783-.57-.38-1.81.588-1.81h3.461a1 1 0 00.951-.69l1.07-3.292z"/>
              </svg>
            {% endfor %}
          </div>
          <span class="hv-rating-text">(4.8) • 127 avis</span>
        </div>
      </div>

      <!-- Section Prix -->
      <div class="hv-price-section">
        <div class="hv-price-container">
          <span class="hv-price-current" id="product-price">{{ product.price | money }}</span>
          {% if product.compare_at_price > product.price %}
            <span class="hv-price-compare">{{ product.compare_at_price | money }}</span>
            {% assign savings = product.compare_at_price | minus: product.price %}
            {% assign savings_percent = savings | times: 100 | divided_by: product.compare_at_price %}
            <span class="hv-savings">-{{ savings_percent }}%</span>
          {% endif %}
        </div>
        {% if product.available %}
          <div style="color: #10B981; font-weight: 600; font-size: 0.9rem;">✓ En stock - Expédition immédiate</div>
        {% else %}
          <div style="color: #EF4444; font-weight: 600; font-size: 0.9rem;">⚠ Rupture de stock</div>
        {% endif %}
      </div>

      <!-- Formulaire Produit -->
      <form action="/cart/add" method="post" enctype="multipart/form-data" id="AddToCartForm">
        
        <!-- Variants -->
        {% unless product.has_only_default_variant %}
          {% for option in product.options_with_values %}
            <div class="hv-variant-section">
              <div class="hv-variant-title">{{ option.name }}:</div>
              <div class="hv-variant-options">
                {% for value in option.values %}
                  <label class="hv-variant-option">
                    <input type="radio" 
                           name="options[{{ option.name }}]" 
                           value="{{ value | escape }}" 
                           {% if forloop.first %}checked{% endif %}
                           style="display: none;">
                    <span>{{ value }}</span>
                  </label>
                {% endfor %}
              </div>
            </div>
          {% endfor %}
        {% endunless %}

        <!-- Quantité -->
        <div class="hv-quantity-container">
          <label class="hv-quantity-label" for="Quantity">Quantité:</label>
          <div class="hv-quantity-selector">
            <button type="button" class="hv-qty-btn" onclick="decreaseQuantity()">−</button>
            <input type="number" 
                   id="Quantity" 
                   name="quantity" 
                   value="1" 
                   min="1" 
                   class="hv-qty-input">
            <button type="button" class="hv-qty-btn" onclick="increaseQuantity()">+</button>
          </div>
        </div>

        <!-- Boutons CTA -->
        <div class="hv-cta-section">
          <button type="submit" 
                  name="add" 
                  class="hv-add-to-cart" 
                  {% unless product.available %}disabled{% endunless %}>
            <svg width="20" height="20" fill="currentColor" viewBox="0 0 20 20">
              <path d="M3 1a1 1 0 000 2h1.22l.305 1.222a.997.997 0 00.01.042l1.358 5.43-.893.892C3.74 11.846 4.632 14 6.414 14H15a1 1 0 000-2H6.414l1-1H14a1 1 0 00.894-.553l3-6A1 1 0 0017 3H6.28l-.31-1.243A1 1 0 005 1H3zM16 16.5a1.5 1.5 0 11-3 0 1.5 1.5 0 013 0zM6.5 18a1.5 1.5 0 100-3 1.5 1.5 0 000 3z"/>
            </svg>
            {% if product.available %}
              Ajouter au panier • {{ product.price | money }}
            {% else %}
              Rupture de stock
            {% endif %}
          </button>
          
          {% if product.available %}
            <button type="button" class="hv-buy-now" onclick="buyNow()">
              Acheter maintenant
            </button>
          {% endif %}
        </div>
      </form>

      <!-- Description -->
      {% if product.description != blank %}
        <div class="hv-product-description">
          <h3 class="hv-description-title">Description</h3>
          <div class="hv-description-content">
            {{ product.description }}
          </div>
        </div>
      {% endif %}

      <!-- Specifications -->
      <div class="hv-product-specs">
        <h3 class="hv-specs-title">Caractéristiques</h3>
        <div class="hv-specs-grid">
          {% if product.vendor != blank %}
            <div class="hv-spec-item">
              <span class="hv-spec-label">Marque:</span>
              <span class="hv-spec-value">{{ product.vendor }}</span>
            </div>
          {% endif %}
          {% if product.type != blank %}
            <div class="hv-spec-item">
              <span class="hv-spec-label">Type:</span>
              <span class="hv-spec-value">{{ product.type }}</span>
            </div>
          {% endif %}
          <div class="hv-spec-item">
            <span class="hv-spec-label">Référence:</span>
            <span class="hv-spec-value">{{ product.handle | upcase }}</span>
          </div>
          <div class="hv-spec-item">
            <span class="hv-spec-label">Disponibilité:</span>
            <span class="hv-spec-value">
              {% if product.available %}En stock{% else %}Rupture{% endif %}
            </span>
          </div>
        </div>
      </div>
    </div>
  </div>
</div>

<!-- JavaScript pour interactions -->
<script>
document.addEventListener('DOMContentLoaded', function() {
  // Gestion des variants
  const variantOptions = document.querySelectorAll('.hv-variant-option');
  variantOptions.forEach(option => {
    option.addEventListener('click', function() {
      const radioInput = this.querySelector('input[type="radio"]');
      radioInput.checked = true;
      
      // Remove active class from siblings
      this.parentElement.querySelectorAll('.hv-variant-option').forEach(opt => {
        opt.classList.remove('selected');
      });
      
      // Add active class
      this.classList.add('selected');
      
      // Update price if needed
      updateProductPrice();
    });
  });
  
  // Initialiser le premier variant comme sélectionné
  variantOptions.forEach(option => {
    const radioInput = option.querySelector('input[type="radio"]');
    if (radioInput.checked) {
      option.classList.add('selected');
    }
  });
});

// Changer l'image principale
function changeMainImage(imageUrl, thumbnail) {
  const mainImage = document.getElementById('main-product-image');
  mainImage.src = imageUrl;
  
  // Update active thumbnail
  document.querySelectorAll('.hv-thumbnail').forEach(thumb => {
    thumb.classList.remove('active');
  });
  thumbnail.classList.add('active');
}

// Quantité
function increaseQuantity() {
  const input = document.getElementById('Quantity');
  input.value = parseInt(input.value) + 1;
}

function decreaseQuantity() {
  const input = document.getElementById('Quantity');
  if (parseInt(input.value) > 1) {
    input.value = parseInt(input.value) - 1;
  }
}

// Buy Now (redirect to checkout)
function buyNow() {
  // Ajouter au panier puis rediriger vers checkout
  document.getElementById('AddToCartForm').addEventListener('submit', function(e) {
    e.preventDefault();
    // Logic pour buy now
    window.location.href = '/checkout';
  });
  document.getElementById('AddToCartForm').submit();
}

// Update product price based on variants
function updateProductPrice() {
  // Cette fonction peut être étendue pour gérer les prix de variants
  console.log('Price updated for selected variant');
}

// Animation d'ajout au panier
document.getElementById('AddToCartForm').addEventListener('submit', function(e) {
  const button = this.querySelector('.hv-add-to-cart');
  const originalText = button.innerHTML;
  
  button.innerHTML = `
    <svg width="20" height="20" fill="currentColor" viewBox="0 0 20 20" style="animation: spin 1s linear infinite;">
      <path d="M4 2a1 1 0 011 1v2.101a7.002 7.002 0 0111.601 2.566 1 1 0 11-1.885.666A5.002 5.002 0 005.999 7H9a1 1 0 010 2H4a1 1 0 01-1-1V3a1 1 0 011-1zm.008 9.057a1 1 0 011.276.61A5.002 5.002 0 0014.001 13H11a1 1 0 110-2h5a1 1 0 011 1v5a1 1 0 11-2 0v-2.101a7.002 7.002 0 01-11.601-2.566 1 1 0 01.61-1.276z"/>
    </svg>
    Ajout en cours...
  `;
  
  // Simuler l'ajout
  setTimeout(() => {
    button.innerHTML = `
      <svg width="20" height="20" fill="currentColor" viewBox="0 0 20 20">
        <path fill-rule="evenodd" d="M16.707 5.293a1 1 0 010 1.414l-8 8a1 1 0 01-1.414 0l-4-4a1 1 0 011.414-1.414L8 12.586l7.293-7.293a1 1 0 011.414 0z" clip-rule="evenodd"/>
      </svg>
      Ajouté au panier !
    `;
    
    setTimeout(() => {
      button.innerHTML = originalText;
    }, 2000);
  }, 1000);
});
</script>

<style>
@keyframes spin {
  from { transform: rotate(0deg); }
  to { transform: rotate(360deg); }
}
</style>
