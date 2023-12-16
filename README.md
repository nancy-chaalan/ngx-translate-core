# ngx-translate-core
ngx translator for angular project, to translate your project in the simplest way to any language you want, just download the project and check the steps.

Overview
This guide provides a step-by-step process to integrate NGX-Translate into your Angular application for multilingual support. NGX-Translate is a powerful library for handling translations in Angular projects.

=========== Step 1: Install NGX-Translate
Run the following command in your terminal to install the necessary packages:

npm install @ngx-translate/core @ngx-translate/http-loader


@ngx-translate/core: Contains core routines for translation, including TranslateService and the translate pipe.
@ngx-translate/http-loader: Loads translation files dynamically from your web server.


=========== Step 2: Set up TranslateModule and TranslateService
Modify app.module.ts
typescript
Copy code
import { NgModule } from '@angular/core';
import { BrowserModule } from '@angular/platform-browser';
import { HttpClientModule, HttpClient } from '@angular/common/http';
import { TranslateLoader, TranslateModule } from '@ngx-translate/core';
import { TranslateHttpLoader } from '@ngx-translate/http-loader';

import { AppComponent } from './app.component';

@NgModule({
  declarations: [AppComponent],
  imports: [
    BrowserModule,
    HttpClientModule,
    TranslateModule.forRoot({
      loader: {
        provide: TranslateLoader,
        useFactory: HttpLoaderFactory,
        deps: [HttpClient],
      },
    }),
  ],
  providers: [],
  bootstrap: [AppComponent],
})
export class AppModule {}

export function HttpLoaderFactory(http: HttpClient): TranslateHttpLoader {
  return new TranslateHttpLoader(http);
}
Modify app.component.ts
typescript
Copy code
import { Component } from '@angular/core';
import { TranslateService } from '@ngx-translate/core';

@Component({
  selector: 'app-root',
  templateUrl: './app.component.html',
  styleUrls: ['./app.component.scss'],
})
export class AppComponent {
  constructor(private translate: TranslateService) {
    translate.setDefaultLang('en');
    translate.use('en');
  }
} 


=========== Step 3: Create JSON Translation Files
Create empty translation files for each language in the following locations:

assets/i18n/de.json
assets/i18n/en.json
assets/i18n/fr.json
For now, keep these files empty or provide placeholder content.
