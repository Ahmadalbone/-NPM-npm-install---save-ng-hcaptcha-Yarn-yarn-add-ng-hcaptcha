# NPM
npm install --save ng-hcaptcha

# Yarn
yarn add ng-hcaptcha
import { NgHcaptchaModule } from 'ng-hcaptcha';

@NgModule({
    imports: [
        // Option #1
        // Set the sitekey globally for every hCaptcha component
        NgHcaptchaModule.forRoot({
            siteKey: 'YOUR_SITEKEY',
            languageCode: 'de' // optional, will default to browser language
        }),

        // Option #2
        // This option requires you to set the [siteKey] property for every hCaptcha component
        NgHcaptchaModule.forRoot()
    ]
})<!-- Regular usage -->
<ng-hcaptcha (verify)="onVerify($event)"
              (expired)="onExpired($event)"
              (error)="onError($event)">
</ng-hcaptcha>

<!-- Usage in forms -->
<!-- The value of the form control will be the verification token -->
<form [formGroup]="formGroup" (submit)="onSubmit()">
    <ng-hcaptcha formControlName="captcha"></ng-hcaptcha>
</form>

<!-- Invisible captcha -->
<button ngHcaptchaInvisibleButton
        (verify)="onVerify($event)"
        (expired)="onExpired($event)"
        (error)="onError($event)">Click me</button
>onVerify(token: string) {
    // The verification process was successful.
    // You can verify the token on your server now.
}

onExpired(response: any) {
    // The verification expired.
}

onError(error: any) {
    // An error occured during the verification process.
}
