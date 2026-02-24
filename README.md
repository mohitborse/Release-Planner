Step-by-Step: Deploy Angular App to GitHub Pages
1️⃣ Install the Pages deploy package
Open your project folder locally and run:
ng add angular-cli-ghpages

2️⃣ Build your Angular app for production
ng build --configuration production --base-href "https://mohitborse.github.io/Release-Planner/"
✔️ This builds optimized files
✔️ --base-href ensures assets load correctly on GitHub Pages

3️⃣ Deploy to GitHub Pages
Now run:
npx angular-cli-ghpages --dir=dist/release-planner/browser

🎉 That’s It!
Your app should be live at:
👉 https://mohitborse.github.io/Release-Planner/
Give it a minute after deploying — GitHub Pages takes a short moment to publish.

🛠 If Routing Doesn’t Work
Angular apps using path routing often 404 on refresh. Fix it by using HashLocationStrategy:
In app.module.ts:
import { HashLocationStrategy, LocationStrategy } from '@angular/common';
@NgModule({
  providers: [{ provide: LocationStrategy, useClass: HashLocationStrategy }]
})
export class AppModule {}

Optional: Auto Deploy on Push
You can set up GitHub Actions so every git push deploys automatically.


npm install -g angular-cli-ghpages
ng build --configuration production --base-href "https://mohitborse.github.io/Release-Planner/"
npx angular-cli-ghpages --dir=dist/release-planner/browser
