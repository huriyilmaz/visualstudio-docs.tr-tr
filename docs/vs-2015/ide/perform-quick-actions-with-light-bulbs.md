---
title: Hafif bulbs ile hızlı eylemler gerçekleştirme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 990ee487-cf9a-4b89-9784-e7b47c220e8c
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 78ac9b0aba4e56b2240ef65783231d31d77e5144
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72670345"
---
# <a name="perform-quick-actions-with-light-bulbs"></a>Ampullerle hızlı eylemler gerçekleştirme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Hafif bulbs, Visual Studio 2015 ' deki yeni bir üretkenlik özelliğidir. Bunlar, Visual Studio düzenleyicisinde görüntülenen ve yeniden düzenleme hataları da dahil olmak üzere hızlı eylemler gerçekleştirmek için tıklaytıkları simgelerdir. Hafif bulbs hata düzeltme ve yeniden düzenleme yardımını, genellikle yazdığınız satıra göre tek bir odak noktasına getirir.

 ![Küçük ampul simgesi](../ide/media/vs2015-lightbulbsmall.png "VS2015_LightBulbSmall")

 C# ve Visual Basic ' de, kırmızı renkli bir dalgalı çizgi ve Visual Studio 'Nun sorunu nasıl gidereceğiyle ilgili bir önerisi olduğunu gösteren bir ampul görürsünüz. Örneğin, kırmızı renkli bir çizgi ile belirtilen bir hata varsa, bu hata için düzeltmeler kullanılabilir olduğunda bir ampul belirir. C++ ' da, bir üstbilgi dosyasına yeni bir işlev eklediğinizde, bu işlevin saplama uygulamasını oluşturmak için sunulan bir ampul görürsünüz. Herhangi bir dil için üçüncü taraflar, bir SDK 'nın parçası olarak özel tanılama ve öneriler sağlayabilir ve Visual Studio Light bulbs bu kurallara göre ince çalışır.

## <a name="to-see-a-light-bulb"></a>Ampul görmek için

1. Çoğu durumda, bir hata noktasına veya giriş işaretini bir hata içeren bir satıra taşıdığınızda düzenleyicinin sol kenar boşluğunda açık bulbs Sünik bir şekilde görünür. Kırmızı renkli bir çizgi gördüğünüzde, ampulü göstermek için üzerine gelin. Ayrıca, sorunun gerçekleştiği satırdaki herhangi bir yere gitmek için fareyi veya klavyeyi kullandığınızda bir ampul görüntülenmesini de sağlayabilirsiniz.

2. **CTRL +** tuşlarına basın. Açık ampul çağırmak ve doğrudan olası düzeltmeler listesine gitmek için bir satırda herhangi bir yerde.

   ![Fare üzerine gelindiğinde ampul](../ide/media/vs2015-lightbulb-hover.png "VS2015_LightBulb_Hover")

## <a name="to-see-potential-fixes"></a>Olası düzeltmeleri görmek için
 Işığın ampul açısından gidebileceği hızlı eylemlerin bir listesini görüntülemek için aşağı oka veya olası düzeltmeleri göster bağlantısına tıklayın.

 ![Hafif ampul genişletildi](../ide/media/vs2015-lightbulb-hover-expanded.png "VS2015_LightBulb_hover_expanded")

## <a name="to-do-a-refactoring"></a>Yeniden düzenleme yapmak için
 Bağlam menüsünü açmak için sağ tıklayarak yeniden düzenlemeler işlemini gerçekleştirmeye devam edebilirsiniz, ancak CTRL + tuşlarına da basabilirsiniz. yeniden düzenleme seçeneklerini göstermek için. Aşağıdaki çizimde, CTRL + tuşlarına bastıktan sonra ayıklama yöntemi yeniden düzenlemesi sunulmaktadır. çağrıyı içeren satırda bir yerde `Math.Abs` :

 ![Yeniden düzenleme seçeneklerini gösteren ampul](../ide/media/vs2015-lightbulbs-refactor.png "VS2015_LightBulbs_refactor")
