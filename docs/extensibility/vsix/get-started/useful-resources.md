---
title: Yararlı kaynaklar
description: VS genişletilebilirliği dünyasına daha iyi gezinmenize yardımcı olan kullanışlı kaynakların bir listesi.
ms.date: 12/01/2021
ms.topic: conceptual
author: madskristensen
ms.author: madsk
manager: pchapman
ms.prod: visual-studio-windows
ms.technology: vs-ide-sdk
ms.custom: cookbook
ms.openlocfilehash: 713a9e90a5bee2966699db4c53ea7156472852c1
ms.sourcegitcommit: a149b3a034bb555ad217656c0ec8bc1672b1e215
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2021
ms.locfileid: "133516603"
---
# <a name="useful-resources-on-visual-studio-extensions"></a>Visual Studio uzantılarında yararlı kaynaklar

bu kaynaklar Visual Studio genişletilebilirliği dünyayla daha iyi gezinmenize yardımcı olabilir.

aşağıdaki videoda Visual Studio uzantısı yazarları için faydalı kaynaklar sunulmaktadır.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RWP8Kw]

## <a name="resources"></a>Kaynaklar
Bu, uzantınızın yolculuğunda size yardımcı olabilecek bazı faydalı kaynaklar aşağıda verilmiştir.

* [vsıx Community GitHub](https://github.com/VsixCommunity)
* [vsıx Community örnekleri deposu](https://github.com/VsixCommunity/Samples)
* [Resmi VS SDK belgeleri](../../index.yml)
* [VS SDK örnekleri deposu](https://github.com/Microsoft/VSSDK-Extensibility-Samples)
* [Gitter.im üzerinde genişletilebilirlik Chatroom](https://gitter.im/Microsoft/extendvs)

## <a name="know-how-to-search-for-help"></a>Yardım aramanızı öğrenin
Uzantıları yazmak bir sunarak pazarların etkinliğinin bitidir, bu nedenle yardım çevrimiçi aranıyor her zaman ilgili sonuçları döndürmez. Ancak, daha iyi sonuçlar oluşturmak için arama koşullarımızı en iyi hale getirebildiğimiz yollar vardır.

* Arama teriminin bir parçası olarak kesin arabirim ve sınıf adlarını kullanın.
* *vsıx*, *vssdk* veya *Visual Studio* sözcüklerini arama koşullarına eklemeyi deneyin.
* mümkün olduğunda doğrudan GitHub Google/Bing yerine arayın.
* [Gitter.im](https://gitter.im/Microsoft/extendvs) Chatroom 'teki diğer Extender 'lara sorular sorun.

## <a name="use-open-source-as-a-learning-tool"></a>Bir öğrenme aracı olarak açık kaynak kullanma
Büyük olasılıkla uzantınızın ne yapmak istediğinize ve nasıl çalışması gerektiğine dair fikirler vardır. Ancak hangi API 'Leri kullanmanız gerekir ve bunları nasıl doğru bir şekilde nasıl yedeklerirsiniz? Bunlar zor sorulardır ve çok sayıda kişi yanıtlanmadığında bu kullanıcılara verilir.

Market 'teki benzer şeyleri yapan veya ne yapmak istediğinize benzer öğeleri kullanan uzantıları bulmak iyi bir yoldur. Daha sonra bu uzantılara ait kaynak kodunu bulun ve ne olduğunu ve bunların ne olduğunu ve kullandıkları API 'Leri arayın.

## <a name="book"></a>Book
Visual Studio genişletilebilirlik modelini öğrenmeye başlamak için, rishabh verma tarafından [Visual Studio genişletilebilirlik geliştirme](https://www.amazon.com/Visual-Studio-Extensibility-Development-Productivity/dp/1484258525) kitabını göz önünde bulundurun.

:::image type="content" source="../media/book.png" alt-text="genişletilebilirlik geliştirme kitabı kapağı Visual Studio.":::

Bilgi edinmek için kullanılabilecek en iyi kitap.

## <a name="glossary"></a>Sözlük
Bu topluluk araç takımını daha iyi anlamak ve çevrimiçi yardım için arama yapmak üzere, genişletilebilirlik koşullarının paylaşılan bir sözlüğüne sahip olmak kritik öneme sahiptir. Aşağıda, Extender 'ların bilmeleri için önemli olan kavram ve kelimelerin alfabetik bir listesi verilmiştir.

### <a name="dte"></a>MIÞTIR
*EnvDTE, Visual Studio çekirdek otomasyonu için nesneleri ve üyeleri içeren derleme sarmalanmış bir COM kitaplığıdır*. Veya Visual Studio etkileşimde bulunmak için kullanımı kolay bir arabirim.

### <a name="marketplace"></a>Market
[Visual Studio market](https://marketplace.visualstudio.com) , uzantıları dünya genelinde paylaşmak için extender 'lar tarafından kullanılan ortak uzantı deposudur. Microsoft tarafından aittir ve korunur ve tek resmi uzantı Market ' dir.

### <a name="mef"></a>MEF
Managed Extensibility Framework, düzenleyicide Visual Studio-ağırlıklı içinde birkaç bileşen tarafından kullanılır. Uzantı noktalarını bir *paketten* kaydetmek için farklı bir yoldur.

### <a name="package"></a>Paket
Bazen *Paket sınıfı* olarak adlandırılır. `InitializeAsync(...)`uzantınızı başlatmak için Visual Studio yöntemi tarafından çağrılır. Burada olay dinleyicileri ekler ve komutları, araç pencerelerini, ayarları ve diğer şeyleri kaydedebilirsiniz. Derleme sırasında, *paket sınıfındaki* öznitelikler otomatik olarak uzantıya eklenen bir. pkgdef dosyası oluşturmak için kullanılır.

### <a name="pkgdef"></a>. pkgdef
bu, Visual Studio özel kayıt defterine eklenecek anahtarları ve değerleri içeren bir pakettir. Bu dosyayı bir paket sınıfından otomatik olarak oluşturabilir ya da. pkgdef dosyasını el ile oluşturabilir ve `<Asset>` . valtmanifest dosyasına dahil edebilirsiniz.

### <a name="vsct"></a>VSCT
Visual Studio komut tablosu dosyası. Burada menülerin, komutların ve anahtar bağlamalarının bildirildiği yer vardır.

### <a name="vsix"></a>VSıX
bir Visual Studio uzantısının (. vsix) dosya uzantısına ve ayrıca, Visual Studio genişletilebilirlik için bir sözde olan bir unym liğine başvurur.

### <a name="vssdk"></a>VSSDK
*Visual Studio* bu, genel yüzeyi oluşturan sınıflar, hizmetler ve bileşen Visual Studio genişletilebilirlik apı 'sidir. genellikle [Microsoft. VisualStudio. SDK](https://www.nuget.org/packages/Microsoft.VisualStudio.SDK/) NuGet paketine başvururken kullanılır.

[Visual Studio SDK sözlükte](../../visual-studio-sdk-glossary.md)daha fazla bilgi bulabilirsiniz.
