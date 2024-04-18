---
layout: page
title: About Us
permalink: /about/
---

MAKE Roanoke is a non-profit organization dedicated to establishing a community
makerspace in Roanoke, VA.  MAKE Roanoke is run by volunteers.  We are currently
in the process of acquiring space to set up workshops for MAKE Roanoke members.


## Mission Statement

MAKE Roanoke exists to promote knowledge, skill, and creativity in science,
technology, crafts, and the arts. We strive to foster these values in an
inclusive and safe environment. To these ends, MAKE Roanoke shall provide the
following:

 * An inclusive and collegial social framework for members to inspire and
   collaborate with others of similar interests;
 * A maintained communal space providing safe access to tools and supplies for
   projects; and
 * Events to promote education and collaboration between members and the greater
   Roanoke community.

## Super Secret Signup Station

If you would like to be an initial supporter of MAKE Roanoke at $10 per month, sign up here:

<div id="paypal-button-container-P-4AY37020GX411563JMYQGVBA"></div>
<script src="https://www.paypal.com/sdk/js?client-id=AQW23-9eYnJlE8qYmH7NSlhuTA_rXxNtZGGeOiCIEjuAyHCTHe3fH4TEspdUAGNdk2F8-xZULbthoGZP&vault=true&intent=subscription" data-sdk-integration-source="button-factory"></script>
<script>
  paypal.Buttons({
      style: {
          shape: 'rect',
          color: 'gold',
          layout: 'vertical',
          label: 'subscribe'
      },
      createSubscription: function(data, actions) {
        return actions.subscription.create({
          /* Creates the subscription */
          plan_id: 'P-4AY37020GX411563JMYQGVBA'
        });
      },
      onApprove: function(data, actions) {
        alert(data.subscriptionID); // You can add optional success message for the subscriber here
      }
  }).render('#paypal-button-container-P-4AY37020GX411563JMYQGVBA'); // Renders the PayPal button
</script>