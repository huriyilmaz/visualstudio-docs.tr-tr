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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75590299"
---
# <a name="test-a-large-application-with-multiple-ui-maps"></a>Birden çok Kullanıcı Altı Bilgi Yle büyük bir uygulamayı test edin

Bu konu, birden çok Kullanıcı Altı Ay II Eşlemi kullanarak büyük bir uygulamayı sınarken kodlanmış Kullanıcı Altı BirA testinin nasıl kullanılacağını tartışır.

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

**Gereksinimler**

- Visual Studio Enterprise

Yeni bir kodlanmış UI testi oluşturduğunuzda, Visual Studio test çerçevesi varsayılan olarak bir [UIMap](/previous-versions/dd580454(v=vs.140)) sınıfında test için kod oluşturur. Kodlanmış Kullanıcı Arabirimi testlerinin nasıl kaydedilen hakkında daha fazla bilgi için [kodlanmış kullanıcı arabirimi testleri](../test/use-ui-automation-to-test-your-code.md) ve [kodlanmış kullanıcı arabirimi testinin anatomisi](../test/anatomy-of-a-coded-ui-test.md)bölümüne bakın.

UI Haritası için oluşturulan kod, testin etkileşimde bulunduğu her nesne için bir sınıf içerir. Oluşturulan her yöntem için, yöntem parametreleri için bir eşlik sınıfı bu yöntem için özel olarak oluşturulur. Uygulamanızda çok sayıda nesne, sayfa ve form ve denetim varsa, Kullanıcı Bire-posta Haritası çok büyüyebilir. Ayrıca, birkaç kişi testler üzerinde çalışıyorsa, uygulama tek bir büyük Kullanıcı Birleşme Haritası dosyasıyla hantal hale gelir.

Birden çok UI Harita dosyası kullanmak aşağıdaki avantajları sağlayabilir:

- Her harita uygulamanın mantıksal bir alt kümesi ile ilişkili olabilir. Bu, değişikliklerin yönetilmesini kolaylaştırır.

- Her sınayıcı, uygulamanın bir bölümü üzerinde çalışabilir ve uygulamanın diğer bölümlerinde çalışan diğer sınayıcılara müdahale etmeden kodlarını iade edebilir.

- Uygulama Kullanıcı Arabirimi'ne yapılan eklemeler, Kullanıcı Arabirimi'nin diğer bölümleri için testler üzerinde en az etkiyle artımlı olarak ölçeklendirilebilir.

## <a name="do-you-need-multiple-ui-maps"></a>Birden fazla UI Haritasına mı ihtiyacınız var?
Bu tür durumların her birinde birden çok UI Eşlemi oluşturun:

- Bir web sitesindeki kayıt sayfası veya alışveriş sepetinin satın alma sayfası gibi mantıksal bir işlemi birlikte gerçekleştiren birkaç karmaşık bileşik web telefonu denetimi kümesi.

- Uygulamanın çeşitli noktalarından erişilen bağımsız bir denetim kümesi(örneğin, birkaç sayfa işlem içeren bir sihirbaz). Sihirbazın her sayfası özellikle karmaşıksa, her sayfa için ayrı bir Web Sitesi Eşlemi oluşturabilirsiniz.

## <a name="add-multiple-ui-maps"></a>Birden çok UI Eşlem ekleme

### <a name="to-add-a-ui-map-to-your-coded-ui-test-project"></a>Kodlanmış UI test projenize bir UI Haritası eklemek için

1. **Solution**Explorer'da, tüm UI Haritalarını depolamak için kodlanmış UI test projenizde bir klasör oluşturmak için, kodlanmış UI test proje dosyasını sağ tıklatın, **Ekle'ye**işaret edin ve **ardından Yeni Klasör'ü**seçin. Örneğin, adını `UIMaps`verebilirsiniz.

    Yeni klasör, kodlanmış UI test projesi altında görüntülenir.

2. Klasöre `UIMaps` sağ tıklayın, **Ekle'ye**işaret edin ve ardından **Yeni Öğe'yi**seçin.

    **Yeni Öğe Ekle** iletişim kutusu görüntülenir.

   > [!NOTE]
   > Yeni bir kodlanmış UI test eşlemesi eklemek için kodlanmış bir UI test projesinde olmalısınız.

3. Listeden **Kodlu UI Test Haritası'nı** seçin.

    **Ad** kutusuna, yeni Kullanıcı Arabirimi Haritası için bir ad girin. Örneğin, haritanın göstereceği bileşenin veya sayfanın `HomePageMap`adını kullanın.

4. **Ekle'yi**seçin.

    Visual Studio penceresi en aza indirir ve **Kodlu UI Test Builder** iletişim kutusu görüntülenir.

5. İlk yöntem için eylemleri kaydedin ve **Kod Oluştur'u**seçin.

6. İlk bileşen veya sayfaiçin tüm eylemleri ve iddiaları kaydettikten ve yöntemlerhalinde gruplandırdıktan sonra, **Kodlanmış UI Test Builder** iletişim kutusunu kapatın.

7. UI Eşlemleri oluşturmaya devam edin. Eylemleri ve iddiaları kaydedin, bunları her bileşen için yöntemler halinde gruplayın ve ardından kodu oluşturun.

   Çoğu durumda, uygulamanızın üst düzey penceresi tüm sihirbazlar, formlar ve sayfalar için sabit kalır. Her Kullanıcı Arabirimi Haritası'nın üst düzey pencere için bir sınıfı olsa da, tüm haritalar büyük olasılıkla uygulamanızın tüm bileşenlerinin çalıştığı aynı üst düzey pencereye atıfta bulunuyor. Kodlanmış Kullanıcı Arabirimi, üst düzey pencereden başlayarak denetimleri hiyerarşik olarak arar, böylece karmaşık bir uygulamada gerçek üst düzey pencere her Kullanıcı Arabirimi Haritası'nda çoğaltılabilir. Gerçek üst düzey pencere yinelenirse, bu pencere değişirse birden çok değişiklik olur. Bu, UI Haritalar arasında geçiş yaptığınızda performans sorunlarına neden olabilir.

   Bu etkiyi en aza `CopyFrom()` indirmek için, ui eşlemindeki yeni üst düzey pencerenin ana üst düzey pencereyle aynı olduğundan emin olmak için yöntemi kullanabilirsiniz.

## <a name="example"></a>Örnek

Aşağıdaki örnek, çeşitli Kullanıcı Arabirimi Eşlemlerinde oluşturulan sınıflar tarafından temsil edilen her bileşene ve alt denetimlerine erişim sağlayan bir yardımcı program sınıfının parçasıdır.

Bu örnekte, adlı `Contoso` bir web uygulamasında Ana Sayfa, Ürün Sayfası ve Alışveriş Sepeti Sayfası vardır. Bu sayfaların her biri, tarayıcı penceresi olan ortak bir üst düzey pencereyi paylaşır. Her sayfa için bir Web-Servis Aracı Haritası vardır ve yardımcı program sınıfının aşağıdakilere benzer bir kodu vardır:

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

- [Uımap](/previous-versions/dd580454(v=vs.140))
- <xref:Microsoft.VisualStudio.TestTools.UITesting.BrowserWindow.CopyFrom%2A>
- [Kodunuzu test etmek için UI otomasyonunu kullanma](../test/use-ui-automation-to-test-your-code.md)
- [Kodlanmış UI testleri oluşturma](../test/use-ui-automation-to-test-your-code.md)
- [Kodlanmış ui testinin anatomisi](../test/anatomy-of-a-coded-ui-test.md)
