---
title: Mac için Visual Studio test araçları
description: Mac için Visual Studio kullanarak test oluşturma ve çalıştırma.
ms.date: 11/09/2020
ms.topic: conceptual
helpviewer_keywords:
- testing tools [Visual Studio for Mac]
- unit tests [Visual Studio for Mac]
ms.author: jomatthi
author: jmatthiesen
ms.openlocfilehash: e3c35eae5b3ad48dbbde3b343aaec72573f2b9f4e0aee4f99a0b930d7420bb27
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121437655"
---
# <a name="testing-tools-in-visual-studio-for-mac"></a>Mac için Visual Studio'de test Mac için Visual Studio

Mac için Visual Studio test araçları, siz ve takımınıza yüksek kod mükemmelliği standartları geliştirmenize ve sürdürmenize yardımcı olabilir. Birim testleri Microsoft birim testi çerçevesi (MSTest), xUnit veya NUnit kullanılarak yazıldığı ve çalıştırıldığı.

## <a name="creating-tests"></a>Test oluşturma
Teste başlamanız için çözümünüze sağ tıklar ve Yeni ekle... menüsünü seçerek > **yeni bir test Project oluşturabilirsiniz.** Ardından iletişim kutusunun sol tarafındaki Test kategorilerinden birini seçin (Örneğin, Web ve Konsol **> Testler kategorisi).** Oluşturmak istediğiniz test projesi türünü seçin ve Ardından'ya tıklayın. Görünen iletişim kutularına yönergeleri izleyin ve ardından çözümünüze yeni bir test projesi eklenir.

![xUnit, MSTest ve NUnit projelerini gösteren Web ve Konsol > Testleri bölümünün seçili olduğu yeni proje iletişim kutusu](media/create-new-test-project.PNG)

> [!NOTE]
> .NET Core uygulamalarınızı birim testi ve birim testi çerçevelerini seçme hakkında daha fazla bilgi için [.NET Core'da birim](/dotnet/core/testing/?pivots=xunit) testi ve .NET Standard bakın.

## <a name="running-tests"></a>Testleri çalıştırma
Birim **Testleri penceresi** birim testlerini çalıştırmak için kullanılır ve Testleri Görüntüle menüsü **>** açılır. Çözümünüzde birim testleri otomatik olarak keşfedilir ve bu pencerede gösterilir. Burada tüm testleri veya seçtiğiniz bir dizi testi çalıştırabilirsiniz.

![Birim testlerinin listesini ve testleri çalıştırmaya veya durdurmaya yönelik araç çubuğunu gösteren Test Penceresi.](media/test-window.PNG)

Birim testleri içeren bir C# sınıfını düzenlerken, test sınıfına veya bir test yöntemine sağ tıklar ve Testleri Çalıştır **veya** Testlerde Hata Ayıkla menüsünü seçerek **testleri çalıştırabilirsiniz.** Testleri **Çalıştır menü** öğesinin seçimi test penceresinde testleri çalıştıracak, Hata Ayıklama **Testlerinin** menüsü seçerek aynı işlem yapılacak ve kodda sorun giderebilirsiniz.

![Çalıştır ve Testlerde Hata Ayıkla seçeneklerinin yer alan düzenleyici sağ tıklama menüsü](media/run-tests-context-menu.PNG)

Testler çalışıyorken, **başarılı Test Sonuçları** başarısız testleri ve bu testleri çalıştırmanın çıkışını gözden geçirebilirsiniz.

![Bir başarısız test ve 21 başarılı test ve 1 başarısız test sayısını gösteren test sonuçları penceresi.](media/test-results-window.PNG)

## <a name="see-also"></a>Ayrıca bkz.

- [.NET Core ve .NET Standard'da birim testi](/dotnet/core/testing)
- [Başlarken testiyle (Visual Studio üzerinde Windows)](/visualstudio/test/getting-started-with-unit-testing)
- [Birim testi temelleri (Visual Studio üzerinde Windows)](/visualstudio/test/unit-test-basics)