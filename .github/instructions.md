# Shopify project
to run local executes:

shopify theme dev --store happy-fantasy-3.myshopify.com

it's going to run on port :9292

# Product page's form

Phase 1: Hide the .pl-hero__actions's form. Keep only the CTA button.

Phase 2: Create a modal that contains the pl-hero__actions's form's code. Such modal must contain an CTA button that when pressed going to submit the infos and redirect user to the Checkout's page. As it does now.

Phase 3: Keep the state. Behavior in case of close. If the user filled some inputs, but closed the modal, and the user opened it again, then the modal should open with field pre filled. 

Phase 4: Urgency form sync — There's a second form (#pl-form-urgency) at the bottom of the page with hidden inputs that mirror the hero fields. The current JS syncs values on every input event. The spec doesn't mention how this sync should work once the form lives inside a modal. If the user fills the modal and closes it, the urgency form's hidden inputs should be updated immediately (on input).

Phase 5: WhatsApp input mask — The inline JS applies a phone mask (XX) XXXXX-XXXX to the WhatsApp field. This mask must be re-bound (or remain bound) when the form moves into the modal DOM.

Phase 6: Accessibility:
Focus trap inside the modal (Tab/Shift+Tab cycling)
Focus on the first non-filled field on open modal
ESC key to close
Returning focus to the CTA button that opened the modal
role="dialog", aria-modal="true", aria-label on the modal
The theme already has ModalDialog + trapFocus() in global.js. So use it if possible.

Phase 7: Variant unavailability — The current CTA button is disabled when product.selected_or_first_available_variant.available is false. The CTA that opens the modal should be enabled. The modal's submit button should be disabled.

Phase 8: Form validation UX — The form uses native HTML validation (required, pattern). If the user clicks submit with invalid fields, Native validation should act.

Phase 9: Mobile presentation — Should the modal be full-screen on mobile.


# Product's page

@playwright
Phase 1: Open product's page. Open the product's page on development mode that's running at localhost:9292.

Phase 2: Reproduce resolution: The runner should list the Brazil top 10 most used smartphone's resolutions, and for each resolution it should adjust the product's page layout to fit these six elements:
1. Menu bar
2. .pl-hero__title
3. .pl-hero__subtitle
4. .pl-hero__price-row
5. .pl-hero__actions
6. .pl-hero__trust

Phase 3: No scroll: Such six elements should be render at the first render of the page, the expected result is that the users of the site don't need to scroll the page to see the CTA button. If needed, reduce the vertical size or even the horizontal size of the video.