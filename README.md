### Fix: DNSPod DNS API2.0 -> API3.0 ——update 2023.1.3
   [API 2.0 offline](https://cloud.tencent.com/document/product/1278/82311) By github@z0z0r4
   
### Support ipv4/ipv6 ——update 2022.12.19
> Changes:

   1. modify **`.github/workflows/run.yml`**

   2. add secret **`DOMAINSV6`**
### Support HUAWEIcloud DNS ——update 2022.10.25
> Usage:

   1. install denpendencies **`pip install -r requirements.txt`**

   2. edit config **`DNS_SERVER`** **`SECRETID`**  **`SECRETKEY`** **`REGION_HW`**

### Support Ipv6 ——update 2022.07.06
> Usage:

​	just change parm `TYPE` 

### add 'default' ——update 2021.12.15

If you need to use the default circuit，Please remove or change the cname record of the default line to another line

param for 'default'：DEF

param for 'abroad'：AB

### Faker GFW ——update 2021.08.08

> how:

​	add **`fgfw`** to your key, then you will get the latest personal well-selected IPs. Because of the more hardware/net resources it will consumed, each operator will only take 2 ip. And it will use more key calls.

***

### Function

Get high-quality Cloudflare IP，And use the API provided by the domain name service provider to resolve to different lines to achieve the effect of website acceleration（only support dnspod and aliyun）。

**details please goto [Author's web](https://blog.hostmonit.com/cloudflare-select-ip-plus/)**


### Usage

>  Requirements: 
>
>  ★ Can use Cloudlfare service but no need to use cloudflare nameserver.
>
>  ★ Python3、pip(if you want to run on your own server)
>
>  ★ API ID(SecretID) and key(SecretKey) from your dns service provider. TencendCloud(dnspod)(https://console.cloud.tencent.com/cam/capi) or Aliyun(https://help.aliyun.com/document_detail/53045.html?spm=a2c4g.11186623.2.11.2c6a2fbdh13O53)


#### Use GitHub Actions 

1. Get your SecretID, SecretKey and authority

2. Fork to your repository ![fork.png](https://img.hostmonit.com/images/2020/11/05/fork.png)

3. Settings->Secrets-New secret，DOMAINS，[DOMAINSV6], KEY，SECRETID，SECRETKEY

   > - DOMAINS  : `{"hostmonit.com": {"@": ["CM","CU","CT"], "shop": ["CM", "CU", "CT"], "stock": ["CM","CU","CT"]},"4096.me": {"@": ["CM","CU","CT"], "vv":["CM","CU","CT"]}}`
   > - DOMAINSV6 : if you need it's the same as DOMAINS
   > - KEY :     API key of cloudflare IP pool，[Store](https://shop.hostmonit.com)purchase KEY，or use the free one `o1zrmHAF` ，but `o1zrmHAF` will not get the latest IP. You can check from [here](https://stock.hostmonit.com/CloudFlareYes)for ip)
   > - SECRETID : DNS_API_ID
   > - SECRETKEY : DNS_API_KEY

   ![secret.png](https://img.hostmonit.com/images/2020/11/05/secret.png)

4. Change the `AFFECT_NUM` and `DNS_SERVER` of  `cf2dns_actions.py`. Modify `.github/workflows/run.yml` the "cron" part. Then enable the github action. That's all, check the Actions.

   ![modify.png](https://img.hostmonit.com/images/2020/11/05/modify.png)


   ![commit.png](https://img.hostmonit.com/images/2020/11/05/commit.png)

   

   ![build.png](https://img.hostmonit.com/images/2020/11/05/build.png)

### Disclaimers

> 1.The network environment is complex, and what suits me may not suit you, so try to try free KEY or buy trial KEY first
>
> 2.If you have any questions or suggestions, please open an issue (to original repository) or email the author, and don't accept abuse, wrangling or roast
>
> 3.Key price is low, just to filter out some people
>
> ★ It may overwrite your current dns resolve settings.

