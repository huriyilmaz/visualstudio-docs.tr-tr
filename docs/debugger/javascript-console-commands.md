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
ms.openlocfilehash: b30b59b95b09cac8308474b2b2963f9b96d58146
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72731704"
---
# <a name="javascript-console-commands-in-visual-studio"></a>Visual Studio 'da JavaScript konsol komutları

Komutları kullanarak, Visual Studio 'nun JavaScript Konsol penceresinde ileti gönderebilir ve diğer görevleri gerçekleştirebilirsiniz. Bu pencerenin nasıl kullanılacağını gösteren örnekler için bkz. [hızlı başlangıç: JavaScript hata ayıklama](../debugger/quickstart-debug-javascript-using-the-console.md?view=vs-2017). Bu konudaki bilgiler, Apache Cordova için Visual Studio Araçları kullanılarak oluşturulan Node.js App, UWP uygulamaları ve uygulamalar için geçerlidir.

JavaScript Konsolu penceresi kapalıysa, Visual Studio 'da hata ayıklama sırasında **Debug**  >  **Windows**  >  **JavaScript Konsolu**Hata Ayıkla ' yı seçerek açabilirsiniz.

> [!NOTE]
> Pencere hata ayıklama oturumu sırasında kullanılamıyorsa, hata ayıklayıcı türünün projenin hata ayıklama özelliklerinde **betik** olarak ayarlandığından emin olun.

Konsolunu Microsoft Edge geliştirici araçları 'nda kullanma hakkında bilgi için [Bu konuya](/microsoft-edge/devtools-guide)bakın.

## <a name="console-object-commands"></a>Konsol nesnesi komutları

Bu tabloda `console` JavaScript Konsol penceresinde kullanabileceğiniz nesne komutlarının söz dizimi ve kodunuzu, koddan konsola göndermek için kullanabileceğiniz sözdizimi gösterilmektedir. Bu nesne, isterseniz bilgilendirici iletileri ve hata mesajlarını ayırt edebilmeniz için bir dizi form sağlar.

`window.console.[command]`Konsol adlı yerel nesnelerle ilgili olası karışıklık oluşmasını önlemek istiyorsanız, daha uzun bir komut formunu kullanabilirsiniz.

> [!TIP]
> Visual Studio 'nun eski sürümleri, tüm komut kümesini desteklemez. Desteklenen komutlar hakkında hızlı bilgi almak için konsol nesnesinde IntelliSense kullanın.

|Komut|Açıklama|Örnek|
|-------------|-----------------|-------------|
|`assert(expression, message)`|`expression` **False**olarak değerlendirilirse bir ileti gönderir.|`console.assert((x == 1), "assert message: x != 1");`|
|`clear()`|Komut dosyası hata iletileri de dahil olmak üzere konsol penceresinden iletileri temizler ve ayrıca konsol penceresinde görünen betiği de temizler. Konsol giriş istemine girdiğiniz betiği temizlemez.|`console.clear();`|
|`count(title)`|Count komutunun konsol penceresine çağrılme sayısını gönderir. Count çağrısı her bir isteğe bağlı tarafından benzersiz şekilde tanımlanır `title` .<br /><br /> Konsol penceresinde Varolan giriş, `title` (varsa) parametresi tarafından tanımlanır ve sayı komutu tarafından güncelleştirilir. Yeni bir giriş oluşturulmaz.|`console.count();`<br /><br /> `console.count("inner loop");`|
|`debug(message)`|`message`Konsol penceresine gönderir.<br /><br /> Bu komut, Console. log ile aynıdır.<br /><br /> Komutu kullanılarak geçirilen nesneler bir dize değerine dönüştürülür.|`console.debug("logging message");`|
|`dir(object)`|Belirtilen nesneyi konsol penceresine gönderir ve bir nesne görselleştiricisi içinde görüntüler. Görselleştiriciyi konsol penceresindeki özellikleri incelemek için kullanabilirsiniz.|`console.dir(obj);`|
|`dirxml(object)`|Belirtilen XML düğümünü `object` konsol penceresine gönderir ve bunu BIR XML düğümü ağacı olarak görüntüler.|`console.dirxaml(xmlNode);`|
|`error(message)`|`message`Konsol penceresine gönderir. İleti metni kırmızı ve bir hata simgesiyle önceden ortaya çıkmış.<br /><br /> Komutu kullanılarak geçirilen nesneler bir dize değerine dönüştürülür.|`console.error("error message");`|
|`group(title)`|Konsol penceresine gönderilen iletiler için bir gruplandırma başlatır ve isteğe bağlı `title` olarak bir grup etiketi gönderir. Gruplar, iç içe olabilir ve konsol penceresinde bir ağaç görünümünde görünebilir.<br /><br /> Grup * komutları, bir bileşen modelinin kullanımda olduğu durumlarda olduğu gibi bazı senaryolarda konsol penceresi çıkışını görüntülemeyi daha kolay hale getirir.|`console.group("Level 2 Header");` <br /> `console.log("Level 2");` <br /> `console.group();` <br /> `console.log("Level 3");` <br /> `console.warn("More of level 3");` <br /> `console.groupEnd();` <br /> `console.log("Back to level 2");` <br /> `console.groupEnd();` <br /> `console.debug("Back to the outer level");`|
|`groupCollapsed(title)`|Konsol penceresine gönderilen iletiler için bir gruplandırma başlatır ve isteğe bağlı `title` olarak bir grup etiketi gönderir. Kullanılarak gönderilen gruplar `groupCollapsed` Varsayılan olarak daraltılmış bir görünümde görünür. Gruplar, iç içe olabilir ve konsol penceresinde bir ağaç görünümünde görünebilir.|Kullanım, `group` komutla aynıdır.<br /><br /> Komut için örneğe bakın `group` .|
|`groupEnd()`|Geçerli grubu sonlandırır.<br /><br /> Gereksinimler:<br /><br /> Visual Studio 2013|Komut için örneğe bakın `group` .|
|`info(message)`|`message`Konsol penceresine gönderir. İleti bir bilgi simgesiyle önceden başlatılacaktır.|`console.info("info message");`<br /><br /> Daha fazla örnek için, bu konunun ilerleyen kısımlarında, bkz. [biçimlendirme konsolu. log output](#ConsoleLog) .|
|`log(message)`|`message`Konsol penceresine gönderir.<br /><br /> Bir nesne geçirirseniz, bu komut bu nesneyi konsol penceresine gönderir ve bir nesne görselleştiricisi içinde görüntüler. Görselleştiriciyi konsol penceresindeki özellikleri incelemek için kullanabilirsiniz.|`console.log("logging message");`|
|`msIsIndependentlyComposed(element)`|Web Apps 'te kullanılır. JavaScript kullanılarak UWP uygulamalarında desteklenmez.|Desteklenmez.|
|`profile(reportName)`|Web Apps 'te kullanılır. JavaScript kullanılarak UWP uygulamalarında desteklenmez.|Desteklenmez.|
|`profileEnd()`|Web Apps 'te kullanılır. JavaScript kullanılarak UWP uygulamalarında desteklenmez.|Desteklenmez.|
|`select(element)`|`element` [DOM Gezgini](../debugger/quickstart-debug-html-and-css.md)'nde belirtilen HTML 'yi seçer.|Console. Select (öğe);|
|`time (name)`|İsteğe bağlı parametre tarafından tanımlanan bir Zamanlayıcı başlatır `name` . İle kullanıldığında `console.timeEnd` , ve arasında geçen süreyi hesaplar `time` `timeEnd` ve sonucu, `name` ön ek olarak dizeyi kullanarak konsola gönderir (MS olarak ölçülür). Performansı ölçmek için uygulama kodunun izleme özelliğini etkinleştirmek için kullanılır.|`console.time("app start");  app.start();  console.timeEnd("app start");`|
|`timeEnd(name)`|İsteğe bağlı parametre tarafından tanımlanan bir süreölçeri sonlandırır `name` . Bkz `time` . konsol komutu.|`console.time("app start"); app.start(); console.timeEnd("app start");`|
|`trace()`|Konsol penceresine bir yığın izlemesi gönderir. İzleme, tam çağrı yığınını içerir ve dosya adı, satır numarası ve sütun numarası gibi bilgileri içerir.|`console.trace();`|
|`warn(message)`|`message`, Bir uyarı simgesiyle önceden ortaya çıkacak konsol penceresine gönderir.<br /><br /> Komutu kullanılarak geçirilen nesneler bir dize değerine dönüştürülür.|`console.warn("warning message");`|

## <a name="miscellaneous-commands"></a>Çeşitli komutlar
Bu komutlar JavaScript Konsol penceresinde de mevcuttur (koddan kullanılamaz).

|Komut|Açıklama|Örnek|
|-------------|-----------------|-------------|
|`$0`, `$1`, `$2`, `$3`, `$4`|Konsol penceresine belirtilen öğeyi döndürür. `$0` DOM Gezgini 'nde Şu anda seçili olan öğeyi döndürür, daha `$1` önce DOM Gezgini 'nde seçili olan öğeyi ve daha sonra dördüncü daha önce seçilmiş olan öğeyi döndürür.|$3|
|`$(id)`|KIMLIĞE göre bir öğe döndürür. Bu `document.getElementById(id)` , `id` öğesi kimliği temsil eden bir dize olan için bir kısayol komutdur.|`$("contenthost")`|
|`$$(selector)`|CSS seçici söz dizimini kullanarak belirtilen seçiciyle eşleşen öğelerin dizisini döndürür. Bu bir kısayol komutdur `document.querySelectorAll()` .|`$$(".itemlist")`|
|`cd()`<br /><br /> `cd(window)`|İfade değerlendirmesinin bağlamını, sayfanın varsayılan en üst düzey penceresinden belirtilen çerçevenin penceresine değiştirmenize olanak sağlar. `cd()`Parametresiz çağırmak, üst düzey pencerenin bağlamını döndürür.|`cd();`<br /><br /> `cd(myframe);`|
|`select(element)`|[DOM Gezgini](../debugger/quickstart-debug-html-and-css.md)'nde belirtilen öğeyi seçer.|`select(document.getElementById("element"));`<br /><br /> `select($("element"));`<br /><br /> `select($1);`|
|`dir(object)`|Belirtilen nesne için bir Görselleştirici döndürür. Görselleştiriciyi konsol penceresindeki özellikleri incelemek için kullanabilirsiniz.|`dir(obj);`|

## <a name="checking-whether-a-console-command-exists"></a>Konsol komutunun mevcut olup olmadığı denetleniyor
Kullanmayı denemeden önce belirli bir komutun mevcut olup olmadığını kontrol edebilirsiniz. Bu örnek, komutun varlığını denetler `console.log` . Varsa `console.log` , kod onu çağırır.

```javascript
if (console && console.log) {
    console.log("msg");
}

```

## <a name="examining-objects-in-the-javascript-console-window"></a>JavaScript Konsol penceresinde nesneleri İnceleme
JavaScript Konsol penceresini kullanırken kapsam içinde olan herhangi bir nesneyle etkileşime geçebilirsiniz. Konsol penceresinde kapsam dışı bir nesneyi incelemek için, `console.log` `console.dir` veya kodunuzda diğer komutları kullanın. Alternatif olarak, kodunuzda bir kesme noktası ayarlayarak (**kesme**noktası Ekle kesme noktası), nesne kapsam içinde olduğunda, nesne ile etkileşim kurabilirsiniz  >  **Insert Breakpoint**.

## <a name="formatting-consolelog-output"></a><a name="ConsoleLog"></a> Biçimlendirme konsolu. log çıktısı
' A birden çok bağımsız değişken geçirirseniz `console.log` , konsol bağımsız değişkenleri bir dizi olarak değerlendirir ve çıktıyı birleştirir.

```javascript
var user = new Object();
user.first = "Fred";
user.last = "Smith";

console.log(user.first, user.last);
// Output:
// Fred Smith

```

`console.log` Ayrıca, çıktıyı biçimlendirmek için "printf" değiştirme desenlerini de destekler. İlk bağımsız değişkende değiştirme desenleri kullanıyorsanız, belirtilen desenleri kullanıldıkları sırada değiştirmek için ek bağımsız değişkenler kullanılacaktır.

 Aşağıdaki değiştirme desenleri desteklenir:

- % s-dize% i-tamsayı% d-tamsayı% f-float% o-nesne% b-ikili% x-onaltılı% e-üs

  Aşağıda değiştirme desenlerinin kullanılmasına ilişkin bazı örnekler verilmiştir `console.log` :

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

## <a name="see-also"></a>Ayrıca bkz.
- [Hızlı Başlangıç: JavaScript hata ayıklama](../debugger/quickstart-debug-javascript-using-the-console.md?view=vs-2017)
- [Hızlı başlangıç: HTML ve CSS hatalarını ayıklama](../debugger/quickstart-debug-html-and-css.md?view=vs-2017)
