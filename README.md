        await axios.get(`http://local.adspower.com:50325/api/v1/browser/start?user_id=${profileId}`).then(async (res) => {
            console.log(res.data);
            if (res.data.code == 0 && res.data.data.ws.puppeteer && res.data.data.ws.puppeteer) {
                try {
                    const browser = await puppeteer.connect(
                        { browserWSEndpoint: res.data.data.ws.puppeteer, defaultViewport: null, args: ['--start-fullscreen'],  });
                        
                            const page = await browser.newPage();
                            await page.goto('https://www.google.com/');
                            await page.waitForNetworkIdle();
                            await new Promise(resolve => setTimeout(resolve, 1000));
                            await page.goto('chrome-extension://nkbihfbeogaeaoehlefnkodbefgpgknn/home.html#unlock');
                            await page.waitForSelector('#password');
                            await page.type('#password', `${password}\n`);
                            await new Promise(resolve => setTimeout(resolve, 1500));

                            await page.goto('chrome-extension://nkbihfbeogaeaoehlefnkodbefgpgknn/home.html#unlock');
                            await page.waitForSelector('#password');
                            await page.type('#password', `${password}\n`);
                            await new Promise(resolve => setTimeout(resolve, 1500));
