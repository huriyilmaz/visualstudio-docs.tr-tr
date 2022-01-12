---
title: Mac için Visual Studio test araçları
description: Mac için Visual Studio kullanarak test oluşturma ve çalıştırma.
ms.date: 11/09/2020
ms.topic: conceptual
helpviewer_keywords:
- testing tools [Visual Studio for Mac]
- unit tests [Visual Studio for Mac]
author: jmatthiesen
ms.author: jomatthi
manager: dominicn
ms.openlocfilehash: 750653e66a04ce6777258d17e2056b408c2e5773
ms.sourcegitcommit: 965372ad0d75f015403c1af508080bf799914ce3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/12/2022
ms.locfileid: "135805734"
---
# <a name="testing-tools-in-visual-studio-for-mac"></a>Mac için Visual Studio 'de test araçları

Mac için Visual Studio test araçları, sizin ve ekibinizin yüksek standartlara sahip kod mükemmelliği geliştirmelerine ve bu konuda yardımcı olabilir. Birim testleri, Microsoft birim testi çerçevesi (MSTest), xUnit veya NUnit kullanılarak yazılabilir ve çalıştırılabilir.

## <a name="creating-tests"></a>Testler oluşturma
teste başlamak için çözümünüze sağ tıklayıp yeni **> Project ekle...** menüsünü seçerek çözümünüzde yeni bir test projesi oluşturabilirsiniz. Ardından, iletişim kutusunun sol tarafındaki test kategorisinden birini seçin (örneğin, **Web ve konsol > testleri** kategorisi). Oluşturmak istediğiniz test projesi türünü seçin ve Ileri ' ye tıklayın. Görüntülenen iletişim kutularındaki yönergeleri izleyin ve ardından çözümünüze yeni bir test projesi eklenir.

![Web ve konsol > Testleri bölümü seçiliyken xUnit, MSTest ve NUnit projelerini gösteren yeni proje iletişim kutusu](media/create-new-test-project.PNG)

> [!NOTE]
> .NET Core uygulamalarınızın birim testi ve birim testi çerçeveleri seçme hakkında daha fazla bilgi için bkz. [.NET Core 'Da birim testi ve .NET Standard](/dotnet/core/testing/?pivots=xunit) belgeleri.

## <a name="running-tests"></a>Testleri çalıştırma
Birim **Testleri penceresi,** birim testlerini çalıştırmak için kullanılır ve **> testleri görüntüle** menüsü kullanılarak açılır. Çözümünüzdeki birim testleri otomatik olarak bulunur ve bu pencerede gösterilir. burada, seçtiğiniz tüm testleri veya testlerin bir kümesini çalıştırabilirsiniz.

![Testleri çalıştırmaya veya durdurmayla ilgili bir araç çubuğunun ve birim testlerinin listesini gösteren test penceresi.](media/test-window.PNG)

Birim testlerini içeren bir C# sınıfını düzenlediğinizde, test sınıfı veya test yöntemi ' ne sağ tıklayarak ve Testleri **Çalıştır** veya **Hata Ayıkla test** et menüsünü seçerek testleri çalıştırabilirsiniz. **Test Çalıştır** menü öğesini seçme, test penceresindeki testleri çalıştıracak ve **hata ayıklama test (ler)** menüsünün belirlenmesi aynı olur ve kodunuzla ilgili sorunları gidermek için hata ayıklayıcıyı ekler.

![Düzenleyici, Çalıştır ve hata ayıkla test seçenekleri ile sağ tıklama menüsü](media/run-tests-context-menu.PNG)

Testler çalışırken, başarılı veya başarısız testleri gözden geçirebilmeniz için **test sonuçları** bir pencere görünür ve bu testleri çalıştırmanın çıkışı.

![Başarısız bir testi ve 21 geçilen test sayısını ve 1 başarısız testi gösteren test sonuçları penceresi.](media/test-results-window.PNG)

## <a name="see-also"></a>Ayrıca bkz.

- [.NET Core ve .NET Standard birim testi](/dotnet/core/testing)
- [birim testi ile Başlarken (Windows Visual Studio)](/visualstudio/test/getting-started-with-unit-testing)
- [birim testi temelleri (Windows Visual Studio)](/visualstudio/test/unit-test-basics)