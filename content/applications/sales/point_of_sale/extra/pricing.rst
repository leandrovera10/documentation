================
Pricing features
================

.. _pos/pricing/discounts:

Discounts
=========

The Discount feature allows users to decrease the price on item lines in POS orders. This is
calculated as a percentage of the products’ sales price, or the cart's total value. Activate the
settings to apply discounts (per line or global) from :menuselection:`Point of Sale -->
Configuration --> Settings`. Then, scroll down to the :guilabel:`Pricing` section, and enable
:guilabel:`Global Discounts` to add a button to set a discount on the entire order, and
:guilabel:`Line Discounts` to allow cashiers to set discounts on specific products in the cart.

.. seealso::
   :doc:`../../sales/products_prices/prices/discounts`

Global Discounts
----------------
To apply a discount on the whole order from the :ref:`POS register <pos/use/open-register>`, click
the :icon:`oi-fw oi-ellipsis-v` (:guilabel:`vertical ellipsis`) icon and :icon:`fa-tag`
:guilabel:`Discount`. Then, set the :guilabel:`Discount Percentage` and click :guilabel:`Confirm`.

Line Discounts
--------------

To set a discount on a specific product, select the product from the cart and click the
:guilabel:`%` cart modifier from the pad. Then, use the numpad to set the discount.

.. note::
   - Adding other products to the cart switches the cart modifier back to :guilabel:`Qty`
     automatically.
   - You can remove a discount by selecting the product from the cart, clicking :guilabel:`%`, and
     :guilabel:`⌫`

.. _pos/pricing/loyalty:

Discount and loyalty programs
=============================

The Odoo **Sales**, **eCommerce**, and **Point of Sale** applications allow users to create loyalty
programs that customers can use for online and in-store shopping. These programs offer more varied,
public, and time-sensitive pricing options than :doc:`pricelists
<../../sales/products_prices/prices/pricing>`.

To activate the feature in the Point of Sale application, go to :menuselection:`Point of Sale -->
Configuration --> Settings`, and activate the :guilabel:`Promotions, Coupons, Gift Card & Loyalty
Program` setting  in the :guilabel:`Pricing` section.

Once activated, :ref:`configure the desired discount and loyalty programs
<sales/products/loyalty-programs>`. These programs are triggered when an order meets the defined
requirements. Depending on the :ref:`program type <sales/pricing_management/program-types>`, rewards
are either applied automatically or manually by the cashier.

.. seealso::
   :doc:`../../sales/products_prices/loyalty_discount`

.. _pos/pricing/loyalty/codes:

Codes
-----

To apply a gift card, discount code, or coupon, click the :icon:`oi-fw oi-ellipsis-v`
(:guilabel:`vertical ellipsis`) icon and select :icon:`fa-barcode` :guilabel:`Enter Code`.

.. note::
   Coupons and next order coupons code are printed directly on the customer receipts.

Promotions
----------

Promotions are fully automated. They are applied to the order as soon as all program conditions
(such as minimum spend or specific products) are met.

Buy X get Y
-----------

When the order qualifies for a **Buy X Get Y** deal, the reward must be added manually. Click the
:icon:`oi-fw oi-ellipsis-v` (:guilabel:`vertical ellipsis`) icon, select :icon:`fa-star`
:guilabel:`Reward`, and choose the desired item from the list.

Loyalty cards
-------------

To track or spend loyalty points, you must first select a customer in the POS register. Once
selected, their :guilabel:`Loyalty Points` are displayed at the bottom of the cart and updated in
real-time.

To redeem points for a reward, click the :icon:`oi-fw oi-ellipsis-v` (:guilabel:`vertical ellipsis`)
icon, select :icon:`fa-star` :guilabel:`Reward`, and choose the desired item from the list.

.. _pos/pricing/pricelists:

Pricelists
==========

Pricelists allow you to automate price adjustments based on specific criteria. You can use them to
set POS-specific prices, create temporary discount periods, reward loyal customers, or offer
bulk-buy discounts.

Configuration
-------------

To enable pricelists in the Point of Sale app:

#. Navigate to :menuselection:`Point of Sale --> Configuration --> Settings`.
#. In the :guilabel:`Pricing` section, activate the :guilabel:`Flexible Pricelists` feature and
   :guilabel:`Save`.
#. Once the page reloads, click :icon:`oi-arrow-right` :guilabel:`Pricelists` to :ref:`configure
   your pricelists <sales/products/pricelist-configuration>`.
#. When configured, return to the :ref:`POS settings <pos/use/settings>` to add all relevant
   pricelists in the :guilabel:`Available` field, and select the one to be used by
   :guilabel:`Default`.

Select pricelists
-----------------

To manually assign a pricelist to an order from the :ref:`POS register <pos/use/open-register>`,
click the :icon:`oi-fw oi-ellipsis-v` (:guilabel:`vertical ellipsis`) icon and the
:icon:`fa-th-list` icon, followed by the currently selected pricelist's name. Then, click the new
pricelist to apply.

.. tip::
   You can also set a pricelist to be selected automatically once a specific :ref:`customer is set
   <pos/use/customers>`. To do so, go to :menuselection:`Point of Sale --> Orders --> Customers`, open
   the customer form, and assign a pricelist in the :guilabel:`Pricelist` field of the
   :guilabel:`Sales` section in the :guilabel:`Sales & Purchase` tab.

.. seealso::
   - :doc:`../../sales/products_prices/prices/pricing`
   - :ref:`How to use pricelists in an ecommerce environment <ecommerce/prices/pricelists>`

.. _pos/pricing/rounding:

Cash rounding
=============

**Cash rounding** is used when the smallest physical currency denomination (the smallest
coin) is higher than the minimum unit of account.

For example, in countries that have phased out one-cent and two-cent coins, businesses
must round the total amount of a cash transaction to the nearest five cents. In Odoo,
each Point of Sale can be individually configured to apply these rounding rules to
bills and receipts.

Configuration
-------------

#. Go to :menuselection:`Point of Sale --> Configuration --> Settings`.
#. In the :guilabel:`Payment` section, enable :guilabel:`Cash Rounding`.
#. Enable the :guilabel:`Apply only on cash methods` checkbox to deactivate the rounding method for
   :doc:`card payments <../payment_methods>`.
#. In the :guilabel:`Rounding Method` field, select an existing method or click :guilabel:`Create`
   to define a new one.

When creating a new rounding method, define the following:

- :guilabel:`Rounding Precision`: The value of the smallest coinage available (e.g., 0.05).
- :guilabel:`Rounding Strategy`: Choose how the adjustment is recorded:

    - :guilabel:`Modify tax amount`: The rounding difference is applied in the taxes section.
    - :guilabel:`Add a rounding line`: The rounding difference is added as a separate line on the
      receipt and the invoice.
- :guilabel:`Profit Account` and :guilabel:`Loss Account`: The accounts used to record the rounding
  differences.
- :guilabel:`Rounding Method`: The tie-breaking rule used to determine the direction of the rounding
  (:guilabel:`Up`, :guilabel:`Down`, or :guilabel:`Nearest`).

.. important::
   Odoo Point of Sale only supports the :guilabel:`Add a rounding line` rounding strategy.

.. example::

   Example: Rounding a $19.92 total with a **rounding precision** of 0.05.

   The final total changes depending on the **Rounding Method** (the tie-breaking rule) selected in
   the configuration:

   +-----------------------+------------------+------------------------------------------+
   | Rounding Method       | Resulting Total  | Logic                                    |
   +=======================+==================+==========================================+
   | :guilabel:`Up`        | **$19.95**       | Always rounds toward the higher value.   |
   +-----------------------+------------------+------------------------------------------+
   | :guilabel:`Down`      | **$19.90**       | Always rounds toward the lower value.    |
   +-----------------------+------------------+------------------------------------------+
   | :guilabel:`Nearest`   | **$19.90**       | Rounds to the nearest 0.05.              |
   +-----------------------+------------------+------------------------------------------+

.. note::
   Rounding only applies to the **Total** of the receipt, not to individual product prices.

.. _pos/pricing/taxes:

Flexible taxes (fiscal positions)
=================================

When running a business, you may need to apply different taxes and record transactions on various
accounts based on the location and type of business of your customers and providers.

The **fiscal positions** feature enables you to establish rules that automatically select the right
taxes and accounts used for each transaction.

.. seealso::
   - :doc:`../../../finance/accounting/taxes/fiscal_positions`
   - :doc:`../../../finance/accounting/taxes`

Configuration
-------------

To enable the feature, go to :menuselection:`Point of Sale --> Configuration --> Settings`, scroll
down to the :guilabel:`Accounting` section, and enable :guilabel:`Flexible Taxes`.

Then, set a default fiscal position that should be applied to all sales in the selected POS in the
:guilabel:`Default` field. You can also add more fiscal positions to choose from in the
:guilabel:`Allowed` field.

According to the :doc:`fiscal localization package <../../../finance/fiscal_localizations>`
activated, several fiscal positions are preconfigured and can be set and used in POS. However, you
can also :ref:`create new fiscal positions <fiscal_positions/configuration>`.

.. note::
   If you do not set a fiscal position, the tax remains as defined in the **customer taxes** field
   on the product form.

Use fiscal positions
--------------------

Open the :ref:`POS register <pos/use/open-register>` to use one of the allowed fiscal positions.
Then, click the :guilabel:`Tax` button next to the **book-shaped** icon and select a fiscal position
from the list. Doing so applies the defined rules automatically to all the products subject to the
chosen fiscal position's regulations.

.. note::
   If a default fiscal position is set, the tax button displays the name of the fiscal position.

.. seealso::
   :doc:`../../../finance/accounting/taxes/fiscal_positions`
