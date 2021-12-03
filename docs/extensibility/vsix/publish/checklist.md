---
title: En iyi yöntemler denetim listesi
description: Uzantınızı yayımlamadan önce en iyi yöntemlere uygun olduğundan emin olmak için bir denetim listesi.
ms.date: 12/01/2021
ms.topic: conceptual
author: madskristensen
ms.author: madsk
manager: pchapman
ms.prod: visual-studio-windows
ms.technology: vs-ide-sdk
ms.custom: cookbook
ms.openlocfilehash: 7fcdb233f5006a4da2bd647a2ae4113696e51eb5
ms.sourcegitcommit: a149b3a034bb555ad217656c0ec8bc1672b1e215
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2021
ms.locfileid: "133516626"
---
# <a name="best-practices-checklist-to-publish-a-visual-studio-extension"></a>Bir uzantıyı yayımlamak için en iyi Visual Studio denetim listesi

Uzantınızı yayımlamadan önce hatırlamanız gerekenlerin listesi Visual Studio.

Aşağıdaki videoda, uzantınızı en iyi şekilde olduğundan emin olmak için en iyi yöntemler tanıtmaktadır.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RWPmjM]

## <a name="adhere-to-threading-rules"></a>İş parçacığı kurallarına uyma
İş parçacığı kullanımıyla ilgili en iyi yöntemlerin yaygın ihlallerini keşfetmenize ve düzeltmenize yardımcı olacak [Microsoft.VisualStudio.SDK.Analyzers](https://www.nuget.org/packages/Microsoft.VisualStudio.SDK.Analyzers/) NuGet paketini VSIX projenize ekleyin.

## <a name="add-high-quality-icon"></a>Yüksek kaliteli ekleme simgesi
Tüm uzantılarla ilişkilendirilmiş bir simge olması gerekir. Simgenin 96 DPI veya daha .png **boyutu 90x90** piksel olan yüksek kaliteli bir dosya olduğundan emin olun. Simgeyi VSIX projenize ekledikten sonra **.vsixmanifest** dosyasına hem Simge hem de Önizleme görüntüsü olarak kaydedin.

## <a name="name-and-description"></a>Ad ve açıklama
Çalışmalar, kısa ve açıklayıcı bir ad ve doğru bir açıklamaya sahip uzantıların kullanıcılar tarafından yüklenme ihtimalinin daha yüksek olduğunu gösteriyor. Adın uzantının ne yaptığının özünü yansıtacak şekilde olduğundan emin olun. **.vsixmanifest dosyasındaki kısa açıklama,** uzantının ne yaptığıyla ilgili beklentiler ayarlamalı. Bu nedenle, hangi sorunları çözeceğini ve hangi temel özelliklere sahip olduğunu kısaca açıklarız.

## <a name="write-good-marketplace-description"></a>İyi bir Market açıklaması yazma
Bu, uzantınızı başarılı yapmak için en önemli şeylerden biri. İyi bir açıklama şunların yer almaktadır:

* Uzantı tarafından eklenen kullanıcı arabiriminin ekran görüntüleri/animasyonlu GIF'leri.
* Tek tek özelliklerin ayrıntılı açıklaması.
* Varsa diğer ayrıntıların bağlantıları.

## <a name="add-license"></a>Lisans ekleme
Bu lisans Market'te, VSIX yükleyicisinde ve Uzantılar ve **Güncelleştirmeler... iletişim kutusunda** gösterilir. Kullanıcıların beklentilerini ayarlamak için her zaman bir lisans belirtilmelidir. Doğru [choosealicense.com](https://choosealicense.com/) bu konuda yardım almak için choosealicense.com'ı kullanın. Lisans, birçok kullanıcı için önemli olan tüm soruları ve belirsizlikleri kaldırmaya yardımcı Visual Studio önemlidir.

## <a name="add-privacy-notice"></a>Gizlilik bildirimi ekleme
Uzantı telemetri gibi verileri veya uzak uç noktayla başka bir şekilde iletişim kurarsa, açıklamaya bu konuda bir not ekleyin.

## <a name="use-knownmonikers-when-possible"></a>Mümkün olduğunda KnownMonikers kullanma
Visual Studio, [KnownMonikers](../../image-service-and-catalog.md) koleksiyonunda bulunan binlerce simgeyle birlikte sunulmaktadır. Komut düğmelerine simge eklerken, bilinen kullanıcılara tanıdık bir tasarım dilinin parçası olduğu için mevcut KnownMonikers simgelerini Visual Studio bakın. Senaryolarınız için doğru adı bulmak için [KnownMonikers](http://glyphlist.azurewebsites.net/knownmonikers/) Explorer uzantısını ve [Bilinen](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.knownmonikersexplorer) Ler'in tam listesini burada bulabilirsiniz.

## <a name="make-it-feel-native-to-vs"></a>VS'de yerel gibi hissetme
Uzantının kullanıcılar için doğal olması için Visual Studio tasarım desenlerini ve ilkelerini izleyin. Ayrıca kötü tasarlanmış kullanıcı arabiriminin neden olduğu dikkat dağıtıcı öğeleri de azaltır. Tüm düğmelerin, menülerin, araç çubuklarının ve araç pencerelerini yalnızca kullanıcı bunları kullanmak için doğru bağlamda olduğunda varsayılan olarak görünür olduğundan emin olun. Uyulmak gereken bazı kurallar vardır:

* Hiçbir zaman yeni bir üst düzey menü (Dosya, Düzenle, ...) öğesinin yanına ekleme.
* Hiçbir düğme, menü ve araç çubuğu, geçerli değil bağlamlarda görünür olmalıdır.
* Otomatik [yükleme](https://github.com/microsoft/VSSDK-Extensibility-Samples/tree/master/AsyncPackageMigration) gerekiyorsa (büyük olasılıkla gerekli değilse), mümkün olduğunca geç yap.
* Otomatik yüklemeye güvenmek yerine komutların görünürlüğünü geçiş yapmak için [VisibilityConstraints](https://github.com/Microsoft/VSSDK-Extensibility-Samples/tree/master/VisibilityConstraints) kullanın.

## <a name="use-proper-version-ranges"></a>Uygun sürüm aralıklarını kullanma
Herkesin yeni uzantınızı kullanabileceğini Visual Studio için Visual Studio 2010'a kadar tüm bu sürümleri desteklemek cazip olabilir. Burada sorun, bunu yaparak uzantının desteklediği en düşük sürümden daha sonra tanıtmış olan API'leri kullanmak mümkün olmayacaktır. Bu yeni API'ler genellikle önemlidir ve hem uzantının performansını hem de güvenilirliğini artırmanıza yardımcı Visual Studio olur.

Hangi sürümlerinin destekley olmadığına karar vermek için Visual Studio önerilerimiz:

* Yalnızca önceki ve geçerli sürümlerini Visual Studio - mümkünse eski sürümleri desteklemez.
* Açık bir sonlandı sürüm aralığı (örneğin, ) `[16.0,)` belirtme. Sürüm aralıkları hakkında daha [fazla bilgi edinebilirsiniz.](https://devblogs.microsoft.com/visualstudio/visual-studio-extensions-and-version-ranges-demystified/)