---
title: Mac için Visual Studio test araçları
ms.date: 08/03/2020
ms.topic: conceptual
helpviewer_keywords:
- testing tools [Visual Studio for Mac]
- unit tests [Visual Studio for Mac]
ms.author: jomatthi
author: jmatthiesen
ms.openlocfilehash: 758bdcb0d854247847e4d0d56152840643402bf4
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/30/2020
ms.locfileid: "91580967"
---
# <a name="testing-tools-in-visual-studio-for-mac"></a>Mac için Visual Studio 'de test araçları

Mac için Visual Studio test araçları, sizin ve ekibinizin yüksek standartlara sahip kod mükemmelliği geliştirmelerine ve bu konuda yardımcı olabilir. Birim testleri, Microsoft birim testi çerçevesi (MSTest), xUnit veya NUnit kullanılarak yazılabilir ve çalıştırılabilir.

## <a name="creating-tests"></a>Testler oluşturma
Teste başlamak için çözümünüze sağ tıklayıp **> yeni proje Ekle...** menüsünü seçerek yeni bir test projesi oluşturabilirsiniz. Ardından, iletişim kutusunun sol tarafındaki test kategorisinden birini seçin (örneğin, **Web ve konsol > testleri** kategorisi). Oluşturmak istediğiniz test projesi türünü seçin ve Ileri ' ye tıklayın. Görüntülenen iletişim kutularındaki yönergeleri izleyin ve ardından çözümünüze yeni bir test projesi eklenir.

![Web ve konsol > Testleri bölümü seçiliyken xUnit, MSTest ve NUnit projelerini gösteren yeni proje iletişim kutusu](media/create-new-test-project.PNG)

> [!NOTE]
> .NET Core uygulamalarınızın birim testi ve birim testi çerçeveleri seçme hakkında daha fazla bilgi için bkz. [.NET Core 'Da birim testi ve .NET Standard](/dotnet/core/testing/?pivots=xunit) belgeleri.

## <a name="running-tests"></a>Testleri çalıştırma
Birim **Testleri penceresi,** birim testlerini çalıştırmak için kullanılır ve **> bölmeleri görüntüle > birim testleri** menüsü kullanılarak açılır. Çözümünüzdeki birim testleri otomatik olarak bulunur ve bu pencerede gösterilir. burada, seçtiğiniz tüm testleri veya testlerin bir kümesini çalıştırabilirsiniz.

![Testleri çalıştırmaya veya durdurmayla ilgili bir araç çubuğunun ve birim testlerinin listesini gösteren test penceresi.](media/test-window.PNG)

Birim testlerini içeren bir C# sınıfını düzenlediğinizde, test sınıfı veya test yöntemi ' ne sağ tıklayarak ve Testleri **Çalıştır** veya **Hata Ayıkla test** et menüsünü seçerek testleri çalıştırabilirsiniz. **Test Çalıştır** menü öğesini seçme, test penceresindeki testleri çalıştıracak ve **hata ayıklama test (ler)** menüsünün belirlenmesi aynı olur ve kodunuzla ilgili sorunları gidermek için hata ayıklayıcıyı ekler.

![Düzenleyici, Çalıştır ve hata ayıkla test seçenekleri ile sağ tıklama menüsü](media/run-tests-context-menu.PNG)

Testler çalışırken, başarılı veya başarısız testleri gözden geçirebilmeniz için **test sonuçları** bir pencere görünür ve bu testleri çalıştırmanın çıkışı.

![Başarısız bir testi ve 21 geçilen test sayısını ve 1 başarısız testi gösteren test sonuçları penceresi.](media/test-results-window.PNG)

## <a name="see-also"></a>Ayrıca bkz.

- [.NET Core ve .NET Standard birim testi](/dotnet/core/testing)
- [Birim testi ile çalışmaya başlama (Windows üzerinde Visual Studio)](/visualstudio/test/getting-started-with-unit-testing)
- [Birim testi temelleri (Windows üzerinde Visual Studio)](/visualstudio/test/unit-test-basics)