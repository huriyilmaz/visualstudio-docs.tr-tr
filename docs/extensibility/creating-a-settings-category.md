---
title: Ayarlar Kategorisi Oluşturma | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- profile settings, creating categories
ms.assetid: 97c88693-05ff-499e-8c43-352ee073dcb7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5f4b2fa9d82181d0eb899bf9680e8a9debd6c50b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739615"
---
# <a name="create-a-settings-category"></a>Ayarlar kategorisi oluşturma

Bu izne bir Visual Studio ayarları kategorisi oluşturun ve değerleri kaydetmek ve ayarları dosyadan değerleri geri yüklemek için kullanabilirsiniz. Ayarlar kategorisi, "özel ayarlar noktası" olarak görünen ilgili özellikler grubudur; diğer bir deyişle, **İçe Ve Dışa** Aktar ayarları sihirbazında bir onay kutusu olarak. **(Araçlar** menüsünde bulabilirsiniz.) Ayarlar bir kategori olarak kaydedilir veya geri yüklenir ve tek tek ayarlar sihirbazda görüntülenmez. Daha fazla bilgi için [Çevre ayarlarına](../ide/environment-settings.md)bakın.

Sınıftan <xref:Microsoft.VisualStudio.Shell.DialogPage> türeterek bir ayarlar kategorisi oluşturursunuz.

Bu izbiyi başlatmak için öncelikle Seçenekler [Oluştur sayfasının](../extensibility/creating-an-options-page.md)ilk bölümünü tamamlamanız gerekir. Ortaya çıkan Seçenekler özellik ızgarası, kategorideki özellikleri incelemenize ve değiştirmenize olanak tanır. Özellik kategorisini ayarlar dosyasına kaydettikten sonra, özellik değerlerinin nasıl depolanır olduğunu görmek için dosyayı incelersiniz.

## <a name="prerequisites"></a>Ön koşullar
 Visual Studio 2015'ten itibaren Visual Studio SDK'yı indirme merkezinden yüklemezsiniz. Visual Studio kurulumunda isteğe bağlı bir özellik olarak yer almaktadır. VS SDK'yı daha sonra da yükleyebilirsiniz. Daha fazla bilgi için Visual [Studio SDK'yı yükleyin.](../extensibility/installing-the-visual-studio-sdk.md)

## <a name="create-a-settings-category"></a>Ayarlar kategorisi oluşturma
 Bu bölümde, ayarlar kategorisinin değerlerini kaydetmek ve geri yüklemek için özel bir ayarlar noktası kullanırsınız.

### <a name="to-create-a-settings-category"></a>Ayarlar kategorisi oluşturmak için

1. Seçenekler [Oluştur sayfasını](../extensibility/creating-an-options-page.md)tamamlayın.

2. *VSPackage.resx* dosyasını açın ve bu üç dize kaynaklarını ekleyin:

    |Adı|Değer|
    |----------|-----------|
    |106|Benim Kategorim|
    |107|Ayarlarım|
    |108|OptionInteger ve OptionFloat|

     Bu, "Kategorim", "Ayarlarım" nesnesi ve kategori açıklaması "OptionInteger ve OptionFloat" kategorisini adlandıran kaynaklar oluşturur.

    > [!NOTE]
    > Bu üçünden yalnızca kategori adı **İçe Ve Dışa Aktar Ayarları** sihirbazında görünmez.

3. *MyToolsOptionsPackage.cs,* aşağıdaki `float` örnekte `OptionFloat` gösterildiği `OptionPageGrid` gibi sınıfa adlandırılmış bir özellik ekleyin.

    ```csharp
    public class OptionPageGrid : DialogPage
    {
        private int optionInt = 256;
        private float optionFloat = 3.14F;

        [Category("My Options")]
        [DisplayName("My Integer option")]
        [Description("My integer option")]
        public int OptionInteger
        {
            get { return optionInt; }
            set { optionInt = value; }
        }
        [Category("My Options")]
        [DisplayName("My Float option")]
        [Description("My float option")]
        public float OptionFloat
        {
            get { return optionFloat; }
            set { optionFloat = value; }
        }
    }
    ```

    > [!NOTE]
    > "Benim Kategorim" adlı `OptionPageGrid` kategori şimdi iki `OptionInteger` `OptionFloat`özellikten oluşur ve .

4. Sınıfa <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> bir kategori ekleyin ve kategori adı "Benim Kategorim" verin, ObjectName "Ayarlarım" verin ve isToolsOptionPage'i doğru ayarlayın. `MyToolsOptionsPackage` CategoryResourceID, objectNameResourceID ve DescriptionResourceID'yi daha önce oluşturulan ilgili dize kaynağı kimliklerine ayarlayın.

    ```csharp
    [ProvideProfileAttribute(typeof(OptionPageGrid),
        "My Category", "My Settings", 106, 107, isToolsOptionPage:true, DescriptionResourceID = 108)]
    ```

5. Projeyi oluşturun ve hata ayıklamaya başlayın. Deneysel örnekte, **Izgara Sayfamın** artık hem karşıcı hem de float değerlerine sahip olduğunu görmeniz gerekir.

## <a name="examine-the-settings-file"></a>Ayarlar dosyasını inceleme
 Bu bölümde, özellik kategorisi değerlerini bir ayarlar dosyasına dışa aktarın. Dosyayı inceler ve değerleri özellik kategorisine geri aktarırsınız.

1. **F5**tuşuna basarak projeyi hata ayıklama modunda başlatın. Bu deneysel örneği başlatır.

2. **Araç** > **Seçenekleri** iletişim kutusunu açın.

3. Sol bölmedeki ağaç görünümünde, **Kategorimi** genişletin ve ardından **Izgara Sayfamı**tıklatın.

4. **OptionFloat** değerini 3,1416 ve **OptionInteger** değerini 12 olarak değiştirin. **Tamam**'a tıklayın.

5. **Araçlar** menüsünde, **Ayarve Dışa**Aktar'ı tıklatın.

     **İçe Ve Dışa** Aktar Ayarları sihirbazı görüntülenir.

6. **Seçili ortam ayarlarını dışa** aktar'ın seçildiğinden emin olun ve sonra **İleri'yi**tıklatın.

     **Dışa Aktarmak Için Ayarları Seç** sayfası görüntülenir.

7. **Ayarlarımı**tıklatın.

     **Açıklama,** **OptionInteger ve OptionFloat**olarak değişir.

8. **Ayarlarım** seçilen tek kategori olduğundan emin olun ve sonra **İleri'yi**tıklatın.

     **Ayarlar Dosyanızın Adı** sayfası görüntülenir.

9. Yeni ayarlar dosyası *MySettings.vssettings'i* adlandırın ve uygun bir dizine kaydedin. **Son**'a tıklayın.

     **Dışa Aktarma Tamamlandı** sayfası, ayarlarınızın başarıyla dışa aktarıldığını bildirir.

10. **Dosya** menüsünde Aç'ı **Open**işaret edin ve ardından **Dosya'yı**tıklatın. *MySettings.vssettings'i* bulun ve açın.

     Dışa aktarılan özellik kategorisini dosyanın aşağıdaki bölümünde bulabilirsiniz (GUID'leriniz farklı olacaktır).

    ```
    <Category name="My Category_My Settings"
          Category="{4802bc3e-3d9d-4591-8201-23d1a05216a6}"
          Package="{6bb6942e-014c-489e-a612-a935680f703d}"
          RegisteredName="My Category_My Settings">
          PackageName="MyToolsOptionsPackage">
       <PropertyValue name="OptionFloat">3.1416</PropertyValue>
       <PropertyValue name="OptionInteger">12</PropertyValue>
    </Category>
    ```

     Tam kategori adının, nesne adının ardından gelen kategori adına bir alt alt alt lık eklenmesiyle oluştuğuna dikkat edin. OptionFloat ve OptionInteger, dışa aktarılan değerleriyle birlikte kategoride görünür.

11. Ayarlar dosyasını değiştirmeden kapatın.

12. **Araçlar** menüsünde **Seçenekler'i**tıklatın, **Kategorimi**genişletin, **Izgara Sayfamı** tıklatın ve **ardından OptionFloat** değerini 1.0 ve **OptionInteger** değerini 1 olarak değiştirin. **Tamam**'a tıklayın.

13. **Araçlar** menüsünde, **Ayarla ve Dışa Aktar'ı**tıklatın, **seçili ortam ayarlarını içe aktar'ı**seçin ve sonra **İleri'yi**tıklatın.

     **Geçerli Ayarları Kaydet** sayfası görüntülenir.

14. **Hayır'ı seçin, yeni ayarlar içe aktarmanız** ve ardından **İleri'yi**tıklatın.

     **Almak için Ayarlar Koleksiyonu seç** sayfası görüntülenir.

15. Ağaç görünümünün **Ayarlar** düğümündeki *Ayarlar.vs settings* dosyasını seçin. Dosya ağaç görünümünde görünmüyorsa, **Gözat'ı** tıklatın ve bulun. **İleri**’ye tıklayın.

     **İçe Aktaracak Ayarları Seç** iletişim kutusu görüntülenir.

16. **Ayarlarım'ın** seçildiğinden emin olun ve ardından **Bitir'i**tıklatın. **Tümsayfayı Al** çubuğu görüntülendiğinde **Kapat'ı**tıklatın.

17. **Araçlar** menüsünde **Seçenekler'i**tıklatın, **Kategorim'i**genişletin, **Izgara Sayfamı** tıklatın ve özellik kategorisi değerlerinin geri yüklendiğini doğrulayın.
