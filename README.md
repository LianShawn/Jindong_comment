# Jindong_comment
#get jindong's comment

#import package
```
import requests
import re
```
#set headers
```
headers = {
    'cookie': '__jdv=122270672%7Cdirect%7C-%7Cnone%7C-%7C1666690689863; shshshfpa=01ce0ba8-e200-4b1e-ed13-13b55549b2d9-1666690693; shshshfpb=x_s13iVj6y6tEY50Rc6omoQ; __jdu=16666906898631444263590; areaId=2; jsavif=1; __jda=122270672.16666906898631444263590.1666690689.1666690689.1666690689.1; __jdc=122270672; shshshfp=6c80be41910f9b15672807704622a97f; token=73cb50faaadc86ecd9760934e2748328,2,925939; __tk=qLJ5sUPiOiSCqIPhNfaAOUNCqUGAOIvfrcq3rfg3rfGAscbfNiqFN2,2,925939; ip_cityCode=2817; ipLoc-djd=2-2817-51973-0; jwotest_product=99; shshshsID=c7405159e7bbbb5c8e49c65e95d5817e_5_1666690962329; __jdb=122270672.5.16666906898631444263590|1.1666690689; 3AB9D23F7A4B3C9B=S3X3GRFDTWAQPYG3OGDDHDXJYECBGDHO576MUNKO2QUQ623JNFGJWI5LOZLRRVVUDJX7AGY3VDEUSWNS6X72QX6N3Q; JSESSIONID=9D0D01D50B8811FB6DF68633E2E84783.s1',
    'sec-fetch-dest': 'script',
    'sec-fetch-mode': 'no-cors',
    'sec-fetch-site': 'same-site',
    'sec-fetch-user': '?1',
    'upgrade-insecure-requests': '1',
    'User-Agent': 'Mozilla/5.0 (Macintosh; Intel Mac OS X 10_14_6) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/106.0.0.0 Safari/537.36'
}
```
#example of find the content
```
pattern = r'"content":"(.*?)".*?"creationTime"'
a = re.findall(pattern,result)
a[1]
```
#because you can only get 100 pages of comments
```
infor_all = []
for i in range(0,100):
    URL= "https://club.jd.com/comment/productPageComments.action?callback=fetchJSON_comment98&productId=100024018753&score=0&sortType=5&page={}&pageSize=10&isShadowSku=0&rid=0&fold=1".format(i)
    result = requests.get(URL, headers=headers).text
    pattern = r'"content":"(.*?)".*?"creationTime"'
    infor = re.findall(pattern,result)
    infor_all+=infor
    print(i)
```
