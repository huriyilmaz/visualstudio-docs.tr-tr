---
title: Birden Çok UI Haritası Bulunan Büyük Uygulamaları Test Etme
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- coded UI tests, multiple UI maps
- coded UI tests, for large applications
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9fa5afd01ad25d4eebdc0b29e924cb2430d9c775
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75590299"
---
# <a name="test-a-large-application-with-multiple-ui-maps"></a>Birden çok UI haritası ile büyük bir uygulamayı test etme

Bu konu, birden çok UI haritası kullanarak büyük bir uygulamayı test ederken kodlanmış UI testlerinin nasıl kullanılacağını anlatmaktadır.

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

**Requirements**

- Visual Studio Enterprise

Yeni bir kodlanmış UI testi oluşturduğunuzda, Visual Studio test çerçevesi bir [UIMap](/previous-versions/dd580454(v=vs.140)) sınıfında varsayılan olarak test için kod üretir. Kodlanmış UI testlerini kaydetme hakkında daha fazla bilgi için bkz. [KODLANMıŞ UI testleri](../test/use-ui-automation-to-test-your-code.md) ve [kodlanmış UI testinin anatomi](../test/anatomy-of-a-coded-ui-test.md)oluşturma.

UI eşlemesi için üretilen kod, testin etkileşimde bulunduğu her bir nesne için bir sınıf içerir. Oluşturulan her yöntem için, yöntem parametreleri için bir yardımcı sınıf özel olarak bu yöntem için oluşturulur. Uygulamanızda çok sayıda nesne, sayfa ve form ve denetim varsa, UI eşlemesi çok büyük genişleyebilir. Ayrıca, birkaç kişi testler üzerinde çalışıyorsa, uygulama tek bir büyük kullanıcı arabirimi eşleme dosyası ile çok daha etkin hale gelir.

Birden çok UI eşleme dosyası kullanmak aşağıdaki avantajları sağlayabilir:

- Her eşleme, uygulamanın bir mantıksal alt kümesiyle ilişkilendirilebilir. Bu, değişikliklerin yönetilmesini kolaylaştırır.

- Her sınayıcı, uygulamanın bir bölümünde çalışabilir ve uygulamanın diğer bölümlerinde çalışan diğer test edicilerin kesintiye uğramadan kendi kodunu iade edebilir.

- Uygulama kullanıcı arabirimine yapılan eklemeler, Kullanıcı arabiriminin diğer bölümleri için testler üzerinde en az etkiyle artımlı olarak ölçeklendirilebilir.

## <a name="do-you-need-multiple-ui-maps"></a>Birden çok UI eşlemesi gerekiyor mu?
Bu tür durumların her birinde birden çok UI haritası oluşturun:

- Birlikte, bir Web sitesindeki kayıt sayfası veya bir alışveriş sepetinin satın alma sayfası gibi mantıksal bir işlem gerçekleştiren çeşitli karmaşık bileşik UI denetimleri kümesi.

- Birkaç işlem sayfasına sahip bir sihirbaz gibi, uygulamanın çeşitli noktalarından erişilen bağımsız bir denetim kümesi. Sihirbazın her sayfası özellikle karmaşıksa, her sayfa için ayrı UI haritaları oluşturabilirsiniz.

## <a name="add-multiple-ui-maps"></a>Birden çok UI haritası ekleme

### <a name="to-add-a-ui-map-to-your-coded-ui-test-project"></a>Kodlanmış UI test projenize bir UI haritası eklemek için

1. **Çözüm Gezgini**' de, tüm UI haritalarını depolamak IÇIN kodlanmış UI test projenizde bir klasör oluşturmak için, kodlanmış UI test projesi dosyasına sağ tıklayın, **Ekle**' nin üzerine gelin ve **Yeni klasör**' ü seçin. Örneğin, `UIMaps`adını yazabilirsiniz.

    Yeni klasör, kodlanmış UI test projesi altında görüntülenir.

2. `UIMaps` klasöre sağ tıklayın, **Ekle**' nin üzerine gelin ve sonra **Yeni öğe**' yi seçin.

    **Yeni Öğe Ekle** iletişim kutusu görüntülenir.

   > [!NOTE]
   > Yeni bir kodlanmış UI test eşlemesi eklemek için kodlanmış UI test projesi içinde olmanız gerekir.

3. Listeden **KODLANMıŞ UI test Haritası** ' nı seçin.

    **Ad** kutusuna yeni kullanıcı arabirimi eşlemesi için bir ad girin. Haritanın temsil ettiği bileşen veya sayfanın adını kullanın, örneğin `HomePageMap`.

4. Seçin **ekleme**.

    Visual Studio penceresi en aza indirir ve **KODLANMıŞ UI Test Oluşturucusu** iletişim kutusu görüntülenir.

5. İlk yöntem için eylemleri kaydedin ve **kod üret**' i seçin.

6. İlk bileşen veya sayfa için tüm eylemleri ve onayları kaydettikten ve bunları yöntemlere göre gruplandırdıktan sonra, **KODLANMıŞ UI Test Oluşturucusu** iletişim kutusunu kapatın.

7. UI haritaları oluşturmaya devam edin. Eylemleri ve onayları kaydedin, bunları her bir bileşen için yöntemlere gruplandırın ve ardından kodu oluşturun.

   Çoğu durumda, uygulamanızın en üst düzey penceresi tüm sihirbazlar, formlar ve sayfalar için sabit kalır. Her kullanıcı arabirimi eşlemesi üst düzey pencere için bir sınıfa sahip olsa da, tüm haritalar muhtemelen uygulamanızın tüm bileşenlerinin çalıştırıldığı en üst düzey pencereye başvurıyordur. Kodlanmış UI testleri, üst düzey pencereden başlayarak yukarı doğru bir şekilde yukarıdan aşağı doğru olan denetimleri arar, bu nedenle karmaşık bir uygulamada, gerçek üst düzey pencere her kullanıcı arabirimi eşlemesinde yinelenebilir. Gerçek üst düzey pencere yinelendiyse, bu pencere değişirse birden çok değişiklik olur. Bu, UI haritaları arasında geçiş yaparken performans sorunlarına neden olabilir.

   Bu etkiyi en aza indirmek için, bu kullanıcı arabirimi eşlemesindeki yeni üst düzey pencerenin ana en üst düzey pencereyle aynı olduğundan emin olmak için `CopyFrom()` yöntemini kullanabilirsiniz.

## <a name="example"></a>Örnek

Aşağıdaki örnek, çeşitli kullanıcı arabirimi haritalarında oluşturulan sınıflar tarafından temsil edilen her bileşene ve onların alt denetimlerine erişim sağlayan bir yardımcı program sınıfının parçasıdır.

Bu örnekte, `Contoso` adlı bir Web uygulamasının bir giriş sayfası, bir ürün sayfası ve bir alışveriş sepeti sayfası vardır. Bu sayfaların her biri, tarayıcı penceresi olan ortak bir üst düzey pencereyi paylaşır. Her sayfa için bir kullanıcı arabirimi haritası vardır ve yardımcı program sınıfının aşağıdakine benzer bir kodu vardır:

```csharp
using ContosoProject.UIMaps;
using ContosoProject.UIMaps.HomePageClasses;
using ContosoProject.UIMaps.ProductPageClasses;
using ContosoProject.UIMaps.ShoppingCartClasses;

namespace ContosoProject
{
    public class TestRunUtility
    {
        // Private fields for the properties
        private HomePage homePage = null;
        private ProductPage productPage = null;
        private ShoppingCart shoppingCart = null;

        public TestRunUtility()
        {
            homePage = new HomePage();
        }

        // Properties that get each UI Map
        public HomePage HomePage
        {
            get { return homePage; }
            set { homePage = value; }
        }

        // Gets the ProductPage from the ProductPageMap.
        public ProductPage ProductPageObject
        {
            get
            {
                if (productPage == null)
                {
                    // Instantiate a new page from the UI Map classes
                    productPage = new ProductPage();

                    // Since the Product Page and Home Page both use
                    // the same browser page as the top level window,
                    // get the top level window properties from the
                    // Home Page.
                    productPage.UIContosoFinalizeWindow.CopyFrom(
                        HomePage.UIContosoWindowsIWindow);
                }
                return productPage;
            }
        }

    // Continue to create properties for each page, getting the
    // page object from the corresponding UI Map and copying the
    // top level window properties from the Home Page.
}
```

## <a name="see-also"></a>Ayrıca bkz.

- [UIMap](/previous-versions/dd580454(v=vs.140))
- <xref:Microsoft.VisualStudio.TestTools.UITesting.BrowserWindow.CopyFrom%2A>
- [UI otomasyonunu kullanarak kodunuzu test etme](../test/use-ui-automation-to-test-your-code.md)
- [Kodlanmış UI testleri oluşturma](../test/use-ui-automation-to-test-your-code.md)
- [Kodlanmış UI testinin anatomumu](../test/anatomy-of-a-coded-ui-test.md)
