---
title: JavaScript
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-javascript
ms.topic: conceptual
ms.assetid: f3eee13e-30e4-4bc1-81f5-058d7e379b75
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 778912c3149f9f146c01dbab15afa4fabeaa49b8
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/10/2020
ms.locfileid: "75852253"
---
# <a name="javascript-in-visual-studio"></a>Visual Studio’da JavaScript
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

JavaScript, Visual Studio'da birinci sınıf bir dildir. Visual Studio IDE'de JavaScript kodu yazarken standart düzenleme yardımlarının (kod parçacıkları, IntelliSense, vb.) çoğunu veya tümünü kullanabilirsiniz. Birçok uygulama türleri ve hizmetler için JavaScript kodu yazabilirsiniz.

 JavaScript dili referans belgeleri için bkz. [JavaScript](https://msdn.microsoft.com/library/d1et7k7c\(v=vs.94\).aspx).

 Belirli uygulama türlerini ve HTML ve JavaScript kullanarak hizmetleri geliştirmek için Visual Studio ya da belirli Visual Studio uzantıları belirli sürümlerini gerekebilir. Aşağıdaki listede, daha fazla bilgi için bağlantılar içerir.

- Apache Cordova kullanarak platformlar arası uygulamalar oluşturmak için [Apache Cordova için Visual Studio Araçları edinin](https://taco.visualstudio.com/docs/install-vs-tools-apache-cordova/).

- Oluşturulacak [Windows Store](https://developer.microsoft.com/), [Windows Phone](https://developer.microsoft.com/)hem de Evrensel uygulamalar (her iki platform destekleyen) [araçları edinin](https://developer.microsoft.com/windows/downloads).

- Bulut tabanlı hizmetler oluşturmak için bkz [Microsoft Azure sitesine](https://azure.microsoft.com/documentation/).

- Web siteleri ve web uygulamaları oluşturmak için [ASP.NET sitesine](https://dotnet.microsoft.com/apps/aspnet/web-apps).

  > [!NOTE]
  > Boş bir ASP.Net Web sitesi oluşturabileceğinizi ve HTML, CSS ve JavaScript programlama için kullanın. Visual Studio'da hata ayıklama ASP.NET tarafından sağlanan Webconfig dosyası etkinleştirir (veya uygulamayı çalıştırdığınızda F12 araçları da kullanabilirsiniz).

  Visual Studio'daki JavaScript düzenleyicisi IntelliSense desteği sunar. Daha fazla bilgi için bkz. [JavaScript IntelliSense](../ide/javascript-intellisense.md).

## <a name="whats-new-in-javascript"></a>Javascript'teki Yenilikler
 Yeni JavaScript özellikleri, aşağıdaki tabloda listelenmiştir.

|Özellik|Açıklama|
|-------------|-----------------|
|Sınıflar|Yeni sözdizimi bildirimini destekler [sınıfları](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Statements/class).|
|Gösterir|[Öneriler](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Promise) daha kolay ve Temizleyicisi zaman uyumsuz kodlama izin verin. Promise oluşturucular desteklenir, bunların ile `all` ve `race` yardımcı program yöntemleri.|
|Yineleyiciler|Artık her ayrı bir özellik değeri için çalıştırılacak deyimleri ile bir özel yineleme kancası çağırma (diziler, dizi benzeri nesneleri ve yineleyiciler dahil) iterable nesneler üzerinde yineleyebilirsiniz. Daha fazla bilgi için [yineleyiciler ve oluşturucular](https://developer.mozilla.org/docs/Web/JavaScript/Guide/Iterators_and_Generators). **Not:** oluşturucuları henüz desteklenmiyor.|
|Ok işlevleri|Ok işlevinde (= >) için toplu değer sözdizimi sağlar `function` bir sözcük özellikleri anahtar sözcüğünü `this` bağlama.|
|Yerleşik nesneler için yeni yöntemler|[Dizi nesnesi](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Array), [matematik nesnesi](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Math), [sayı nesne](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Number), [nesne nesnesi](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object), ve [dize nesnesi](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String) yerleşik nesneler, birçok yeni yardımcı işlevleri ve verileri inceleme ve düzenleme için özellikleri içerir.|
|Nesne sabit değeri geliştirmeleri|Nesneler artık hesaplanan özellikler, kısa yöntemi tanımları ve toplu değer sözdizimi değeri için aynı adlı bir değişken başlatılır özellikleri destekler. Daha fazla bilgi için [nesneleri oluşturma](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object).|
|Proxy'ler|[Proxy'leri](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Proxy) özel davranış nesneler için etkinleştirin.|
|REST parametreleri|REST parametreler ardışık bağımsız değişken bir dizi işlev çağrısında olanak sağlar. Daha fazla bilgi için [işlevleri](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Function).|
|Spread işleci|[Yayılma işleci](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Operators/Spread_operator) (`…`) bağımsız iterable ifadelere genişletir. Örneğin, `a.b(…array)` yaklaşık olarak aynı olduğundan `a.b.apply(a, array)`.|
|Simgeler|[Sembol](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Symbol) nesneler girişim varolan nesne özellikleri, hiçbir istenmeyen görünürlük ve diğer eşgüdümlü olmayan eklemeler kaybetme riski varolan nesnelerle başka kod tarafından eklenecek özellikleri sağlar.|
|Şablon dizeleri|[Şablon dizeleri](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Template_literals) ifadeler değerlendirilir ve bitişik dize sabit değeri izin dize sabitleri sabit değerlerdir.|
|Unicode geliştirmeleri|Geliştirmeler yapılmıştır Unicode desteği. Örneğin, yeni bir kaçış dizisi biçimi astral kod noktası (dörtten fazla onaltılı basamaklar içeren kod noktaları) destekler. Daha fazla bilgi için [özel karakterler](https://developer.mozilla.org/docs/Web/JavaScript/Guide/Regular_Expressions#Types_of_special_characters).|
|WeakSet|A [WeakSet](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/WeakSet) olan başka bir yerde başvurulan değillerse atık olacak nesneleri koleksiyonu.|
