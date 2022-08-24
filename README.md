# Test Automation Samples
A couple of automated tests, JavaScript

### This first example tests for correct page, button function and search field function:

```
describe('eMag.ro', () => {

    it('should have the correct page title', async () => {

       await browser.url('https://www.emag.ro');
       await expect(browser).toHaveTitle('eMAG.ro - Căutarea nu se oprește niciodată');

    });

    it('should contain a cart button', async () => {
        const cartButton = await $('#my_cart');
        await expect(cartButton).toBeDisplayed();

    })

    it('should open eMag Genius page', async () => {
        const geniusButton = await $('[title="Genius"]');
        await geniusButton.click();
        await expect(browser).toHaveTitle('Genius: livrare gratuită și oferte exclusive pe eMAG, Tazz, Fashion Days și Freshful - eMAG.ro');

    })

    it('should have a working search', async () => {
        const searchBox = await $('#searchboxTrigger');
        const searchButton = await $('.searchbox-submit-button');

        await searchBox.setValue('iphone');
        await searchButton.click();
        await expect(browser).toHaveTitle('Cauți iphone? Alege din oferta eMAG.ro');

    });

});
```
