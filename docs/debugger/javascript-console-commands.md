---
title: JavaScript konsol komutları | Microsoft Docs
ms.custom: ''
ms.date: 10/17/2019
ms.topic: reference
helpviewer_keywords:
- JavaScript Console commands [UWP apps]
- JavaScript debugging, console [UWP apps]
- debugging JavaScript, console [UWP apps]
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- uwp
- cordova
ms.openlocfilehash: fead28e60116acb7b2ae311d98e5475c5da3ec35
ms.sourcegitcommit: 8a96a65676fd7a2a03b0803d7eceae65f3fa142b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72588976"
---
# <a name="javascript-console-commands-in-visual-studio"></a>Visual Studio 'da JavaScript konsol komutları

Komutları kullanarak, Visual Studio 'nun JavaScript Konsol penceresinde ileti gönderebilir ve diğer görevleri gerçekleştirebilirsiniz. Bu pencerenin nasıl kullanılacağını gösteren örnekler için bkz. [hızlı başlangıç: JavaScript hata ayıklama](../debugger/quickstart-debug-javascript-using-the-console.md?view=vs-2017). Bu konudaki bilgiler, Apache Cordova için Visual Studio Araçları kullanılarak oluşturulan Node. js uygulaması, UWP uygulamaları ve uygulamalar için geçerlidir.

JavaScript Konsolu penceresi kapalıysa, Visual Studio 'da hata ayıkladığınızda, **hata ayıkla**  > **Windows**  > **JavaScript Konsolu**' nu seçerek açabilirsiniz.

> [!NOTE]
> Pencere hata ayıklama oturumu sırasında kullanılamıyorsa, hata ayıklayıcı türünün projenin hata ayıklama özelliklerinde **betik** olarak ayarlandığından emin olun.

Konsolunu Microsoft Edge geliştirici araçları 'nda kullanma hakkında bilgi için [Bu konuya](/microsoft-edge/devtools-guide)bakın.

## <a name="console-object-commands"></a>Konsol nesnesi komutları

Bu tablo, JavaScript Konsol penceresinde kullanabileceğiniz `console` nesne komutlarının sözdizimini gösterir veya kodu, koddan konsola göndermek için kullanabilirsiniz. Bu nesne, isterseniz bilgilendirici iletileri ve hata mesajlarını ayırt edebilmeniz için bir dizi form sağlar.

Konsol adlı yerel nesnelerle ilgili olası karışıklık oluşmasını önlemek istiyorsanız, daha uzun komut formunu kullanabilirsiniz `window.console.[command]`.

> [!TIP]
> Visual Studio 'nun eski sürümleri, tüm komut kümesini desteklemez. Desteklenen komutlar hakkında hızlı bilgi almak için konsol nesnesinde IntelliSense kullanın.

|Komut|Açıklama|Örnek|
|-------------|-----------------|-------------|
|`assert(expression, message)`|@No__t_0 **false**olarak değerlendirilirse bir ileti gönderir.|`console.assert((x == 1), "assert message: x != 1");`|
|`clear()`|Komut dosyası hata iletileri de dahil olmak üzere konsol penceresinden iletileri temizler ve ayrıca konsol penceresinde görünen betiği de temizler. Konsol giriş istemine girdiğiniz betiği temizlemez.|`console.clear();`|
|`count(title)`|Count komutunun konsol penceresine çağrılme sayısını gönderir. Count çağrısı her bir isteğe bağlı `title` tarafından benzersiz şekilde tanımlanır.<br /><br /> Konsol penceresindeki mevcut giriş, `title` parametresi (varsa) tarafından tanımlanır ve Count komutu tarafından güncellenir. Yeni bir giriş oluşturulmaz.|`console.count();`<br /><br /> `console.count("inner loop");`|
|`debug(message)`|Konsol penceresine `message` gönderir.<br /><br /> Bu komut, Console. log ile aynıdır.<br /><br /> Komutu kullanılarak geçirilen nesneler bir dize değerine dönüştürülür.|`console.debug("logging message");`|
|`dir(object)`|Belirtilen nesneyi konsol penceresine gönderir ve bir nesne görselleştiricisi içinde görüntüler. Görselleştiriciyi konsol penceresindeki özellikleri incelemek için kullanabilirsiniz.|`console.dir(obj);`|
|`dirxml(object)`|Belirtilen XML düğümü `object` konsol penceresine gönderir ve bunu bir XML düğümü ağacı olarak görüntüler.|`console.dirxaml(xmlNode);`|
|`error(message)`|Konsol penceresine `message` gönderir. İleti metni kırmızı ve bir hata simgesiyle önceden ortaya çıkmış.<br /><br /> Komutu kullanılarak geçirilen nesneler bir dize değerine dönüştürülür.|`console.error("error message");`|
|`group(title)`|Konsol penceresine gönderilen iletiler için bir gruplandırma başlatır ve isteğe bağlı `title` bir grup etiketi olarak gönderir. Gruplar, iç içe olabilir ve konsol penceresinde bir ağaç görünümünde görünebilir.<br /><br /> Grup * komutları, bir bileşen modelinin kullanımda olduğu durumlarda olduğu gibi bazı senaryolarda konsol penceresi çıkışını görüntülemeyi daha kolay hale getirir.|`console.group("Level 2 Header");` <br /> `console.log("Level 2");` <br /> `console.group();` <br /> `console.log("Level 3");` <br /> `console.warn("More of level 3");` <br /> `console.groupEnd();` <br /> `console.log("Back to level 2");` <br /> `console.groupEnd();` <br /> `console.debug("Back to the outer level");`|
|`groupCollapsed(title)`|Konsol penceresine gönderilen iletiler için bir gruplandırma başlatır ve isteğe bağlı `title` bir grup etiketi olarak gönderir. @No__t_0 kullanılarak gönderilen gruplar varsayılan olarak daraltılmış bir görünümde görünür. Gruplar, iç içe olabilir ve konsol penceresinde bir ağaç görünümünde görünebilir.|Kullanım, `group` komutuyla aynıdır.<br /><br /> @No__t_0 komutu için örneğe bakın.|
|`groupEnd()`|Geçerli grubu sonlandırır.<br /><br /> Gereklilik<br /><br /> Visual Studio 2013|@No__t_0 komutu için örneğe bakın.|
|`info(message)`|Konsol penceresine `message` gönderir. İleti bir bilgi simgesiyle önceden başlatılacaktır.|`console.info("info message");`<br /><br /> Daha fazla örnek için, bu konunun ilerleyen kısımlarında, bkz. [biçimlendirme konsolu. log output](#ConsoleLog) .|
|`log(message)`|Konsol penceresine `message` gönderir.<br /><br /> Bir nesne geçirirseniz, bu komut bu nesneyi konsol penceresine gönderir ve bir nesne görselleştiricisi içinde görüntüler. Görselleştiriciyi konsol penceresindeki özellikleri incelemek için kullanabilirsiniz.|`console.log("logging message");`|
|`msIsIndependentlyComposed(element)`|Web Apps 'te kullanılır. JavaScript kullanılarak UWP uygulamalarında desteklenmez.|Desteklenmez.|
|`profile(reportName)`|Web Apps 'te kullanılır. JavaScript kullanılarak UWP uygulamalarında desteklenmez.|Desteklenmez.|
|`profileEnd()`|Web Apps 'te kullanılır. JavaScript kullanılarak UWP uygulamalarında desteklenmez.|Desteklenmez.|
|`select(element)`|[DOM Gezgini](../debugger/quickstart-debug-html-and-css.md)'NDE belirtilen HTML `element` seçer.|Console. Select (öğe);|
|`time (name)`|İsteğe bağlı `name` parametresi tarafından tanımlanan bir Zamanlayıcı başlatır. @No__t_0 ile kullanıldığında, `time` ve `timeEnd` arasında geçen süreyi hesaplar ve sonucu bir ön ek olarak `name` dizesini kullanarak konsola gönderir (MS olarak ölçülür). Performansı ölçmek için uygulama kodunun izleme özelliğini etkinleştirmek için kullanılır.|`console.time("app start");  app.start();  console.timeEnd("app start");`|
|`timeEnd(name)`|İsteğe bağlı `name` parametresi tarafından tanımlanan bir zamanlayıcıyı durdur. @No__t_0 konsolu komutuna bakın.|`console.time("app start"); app.start(); console.timeEnd("app start");`|
|`trace()`|Konsol penceresine bir yığın izlemesi gönderir. İzleme, tam çağrı yığınını içerir ve dosya adı, satır numarası ve sütun numarası gibi bilgileri içerir.|`console.trace();`|
|`warn(message)`|@No__t_0, bir uyarı simgesiyle önceden ortaya çıkacak konsol penceresine gönderir.<br /><br /> Komutu kullanılarak geçirilen nesneler bir dize değerine dönüştürülür.|`console.warn("warning message");`|

## <a name="miscellaneous-commands"></a>Çeşitli komutlar
Bu komutlar JavaScript Konsol penceresinde de mevcuttur (koddan kullanılamaz).

|Komut|Açıklama|Örnek|
|-------------|-----------------|-------------|
|`$0`, `$1`, `$2`, `$3`, `$4`|Konsol penceresine belirtilen öğeyi döndürür. `$0`, DOM Gezgini 'nde Şu anda seçili olan öğeyi döndürür `$1`, DOM Gezgini 'nde daha önce seçilmiş olan öğeyi, Yani dördüncü daha önce seçilen öğeye kadar döndürür.|$3|
|`$(id)`|KIMLIĞE göre bir öğe döndürür. Bu, `id` öğe KIMLIĞINI temsil eden bir dize olduğu `document.getElementById(id)` için bir kısayol komutdur.|`$("contenthost")`|
|`$$(selector)`|CSS seçici söz dizimini kullanarak belirtilen seçiciyle eşleşen öğelerin dizisini döndürür. Bu, `document.querySelectorAll()` için bir kısayol komutdur.|`$$(".itemlist")`|
|`cd()`<br /><br /> `cd(window)`|İfade değerlendirmesinin bağlamını, sayfanın varsayılan en üst düzey penceresinden belirtilen çerçevenin penceresine değiştirmenize olanak sağlar. Parametresiz `cd()` çağrılması, üst düzey pencerenin bağlamını döndürür.|`cd();`<br /><br /> `cd(myframe);`|
|`select(element)`|[DOM Gezgini](../debugger/quickstart-debug-html-and-css.md)'nde belirtilen öğeyi seçer.|`select(document.getElementById("element"));`<br /><br /> `select($("element"));`<br /><br /> `select($1);`|
|`dir(object)`|Belirtilen nesne için bir Görselleştirici döndürür. Görselleştiriciyi konsol penceresindeki özellikleri incelemek için kullanabilirsiniz.|`dir(obj);`|

## <a name="checking-whether-a-console-command-exists"></a>Konsol komutunun mevcut olup olmadığı denetleniyor
Kullanmayı denemeden önce belirli bir komutun mevcut olup olmadığını kontrol edebilirsiniz. Bu örnek `console.log` komutunun varlığını denetler. @No__t_0 varsa, kod onu çağırır.

```javascript
if (console && console.log) {
    console.log("msg");
}

```

## <a name="examining-objects-in-the-javascript-console-window"></a>JavaScript Konsol penceresinde nesneleri İnceleme
JavaScript Konsol penceresini kullanırken kapsam içinde olan herhangi bir nesneyle etkileşime geçebilirsiniz. Konsol penceresinde kapsam dışı bir nesneyi incelemek için, kodunuzda `console.log`, `console.dir` veya diğer komutları kullanın. Alternatif olarak, kodunuzda bir kesme noktası ayarlayarak (**kesme** noktası Ekle  >  kesme noktası**Ekle**), nesne kapsam içinde olduğunda, nesne ile etkileşim kurabilirsiniz.

## <a name="ConsoleLog"></a>Biçimlendirme konsolu. log çıktısı
@No__t_0 için birden çok bağımsız değişken geçirirseniz, konsol bağımsız değişkenleri bir dizi olarak değerlendirir ve çıktıyı birleştirir.

```javascript
var user = new Object();
user.first = "Fred";
user.last = "Smith";

console.log(user.first, user.last);
// Output:
// Fred Smith

```

`console.log`, çıktıyı biçimlendirmek için "printf" değiştirme desenlerini de destekler. İlk bağımsız değişkende değiştirme desenleri kullanıyorsanız, belirtilen desenleri kullanıldıkları sırada değiştirmek için ek bağımsız değişkenler kullanılacaktır.

 Aşağıdaki değiştirme desenleri desteklenir:

- % s-dize% i-tamsayı% d-tamsayı% f-float% o-nesne% b-ikili% x-onaltılı% e-üs

  @No__t_0 'de değiştirme desenleri kullanmanın bazı örnekleri aşağıda verilmiştir:

```javascript
var user = new Object();
user.first = "Fred";
user.last = "Smith";
user.age = 10.01;
console.log("Hi, %s %s!", user.first, user.last);
console.log("%s is %i years old!", user.first, user.age);
console.log("%s is %f years old!", user.first, user.age);

// Output:
// Hi, Fred Smith!
// Fred is 10 years old!
// Fred is 10.01 years old!
```

## <a name="see-also"></a>Ayrıca Bkz.
- [Hızlı Başlangıç: JavaScript hata ayıklama](../debugger/quickstart-debug-javascript-using-the-console.md?view=vs-2017)
- [Hızlı başlangıç: HTML ve CSS hatalarını ayıklama](../debugger/quickstart-debug-html-and-css.md?view=vs-2017)
