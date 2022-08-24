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

### This example focuses on correct function of contact form:

```
describe('damarc.ro', () => {

    it('should have working contact form', async () => {

        await browser.url('https://www.damarc.ro');
        
        const contactButton = await $('#menu-item-962')
        await contactButton.click();
        await expect(browser).toHaveTitle('Contact - Damarc');

        const elementRef = await browser.findElement('xpath', '//*[@id="CybotCookiebotDialogBodyLevelButtonAccept"]')
        const cookieButtonOk = await $(elementRef);

        const nameField = await $('#wpforms-20-field_0');

        const emailField = await $('#wpforms-20-field_1');

        const subjectField = await $('#wpforms-20-field_4');

        const messageField = await $('#wpforms-20-field_2');

        const sendButton = await $('#wpforms-submit-20');

        const confirmationMessage = await $('#wpforms-confirmation-20');

        await cookieButtonOk.click();

        await nameField.click({ timeout: 3000 });
        await nameField.setValue('Test_123');
        
        await emailField.click();
        await emailField.setValue('radu.nuta10@gmail.com');

        await subjectField.click();
        await subjectField.setValue('Test_123');

        await messageField.click();
        await messageField.setValue('Test_123');

        await sendButton.click();
        await expect(confirmationMessage).toBeDisplayed();


    })

})

```
