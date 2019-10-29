---
title: 'Nasıl yapılır: bir ana sayfa veya temayı Içeri aktarma | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, importing items
- importing items [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 2c5078d31e2dcb7f11e5c19e0f8cb228e2f75d50
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/28/2019
ms.locfileid: "72984194"
---
# <a name="how-to-import-a-master-page-or-theme"></a>Nasıl yapılır: bir ana sayfa veya temayı Içeri aktarma
  SharePoint sitenizde sayfalara, ana sayfalar ve Temalar oluşturup kullanarak tutarlı bir görünüm verebilirsiniz. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], bu öğeler için şablon sağlamıyor, ancak bunları SharePoint Designer 'da oluşturabilir ve sonra [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]içine aktarabilirsiniz. Daha fazla bilgi için bkz. Microsoft Web sitesinde [yapı taşı: sayfalar ve Kullanıcı arabirimi](/previous-versions/office/developer/sharepoint-2010/ee539040(v=office.14)) .

### <a name="to-import-a-master-page-or-theme"></a>Ana sayfa veya temayı içeri aktarmak için

1. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], bir SharePoint projesi oluşturun veya açın.

     SharePoint projesi oluşturma hakkında daha fazla bilgi için bkz. [SharePoint projesi ve proje öğesi şablonları](../sharepoint/sharepoint-project-and-project-item-templates.md).

2. Menü çubuğunda, **proje**  > **Yeni öğe Ekle**' yi seçin.

3. **Yeni öğe Ekle** iletişim kutusunda, **SharePoint** düğümünü genişletin ve ardından **2010** düğümünü seçin.

4. SharePoint şablonları listesinde **Modül** şablonunu seçin ve ardından modül için bir ad belirleyin.

     Modül, SharePoint 'te belirttiğiniz bir konuma dağıtım için dosyaları (örneğin, ana sayfa veya Tema dosyaları) içerir.

5. Modülünde, *Sample. txt*adlı varsayılan dosyayı silin.

6. Modül düğümünü seçin.

7. Menü çubuğunda, **proje** > **Varolan öğe Ekle**' yi seçin ve ardından Ana sayfa veya tema dosyasını seçin.

     Ana sayfa dosyalarının. Master uzantısı vardır ve tema dosyalarında. thmx uzantısı vardır.

8. Ana sayfa eklediyseniz, modülün özelliklerinde **dağıtım çakışma çözümü** ayarını **Otomatik** olarak değiştirin.

    > [!NOTE]
    > Ana sayfanın adı, varsayılan ana sayfa veya özel ana sayfa olarak işaretlenen varolan bir ana sayfanın adı ile aynıysa hatalar oluşabilir. Bu sorunu çözme hakkında daha fazla bilgi için bkz. [Izlenecek yol: özel bir ana sayfa ve site sayfasını bir görüntüyle Içeri aktarma](../sharepoint/walkthrough-import-a-custom-master-page-and-site-page-with-an-image.md).

9. Modülünde, *Elements. xml*' i açın.

     Eklediğiniz ana sayfaya veya temaya başvuracak şekilde *Elements. xml* dosyasını güncelleştirmeniz gerekir.

10. Ana sayfa için, var olan modül işaretlemesini aşağıdaki biçimlendirme ile değiştirin.

    ```xml
    <Module Name="[Module Name]" Url="_catalogs/masterpage">
        <File Path="[Module Name]\[Master Page Name].master"
          Url="[Master Page Name].master" Type="GhostableInLibrary" />
    </Module>
    ```

     Bir tema için, var olan modül işaretlemesini aşağıdaki biçimlendirme ile değiştirin.

    ```xml
    <Module Name="[Module Name]" Url="_catalogs/theme"
        <File Path="[Module Name]\[Theme Name].thmx" Url="[Theme
          Name].thmx" Type="GhostableInLibrary" />
    </Module>
    ```

     Yer tutucu değerlerini modülün gerçek adlarıyla ve ana sayfa ya da temaya değiştirdiğinizden emin olun.

     `Type="GhostableInLibrary"` özniteliği, öğenin içerik veritabanına eklendiğini ve modülün `Url` özniteliğinin dosyanın SharePoint içerik veritabanında nerede depolanacağını belirtir.

11. Ana sayfanın dağıtım kapsamını değiştirmek için, **Çözüm Gezgini**, özellik tasarımcısında Özellik dosyasını açın ve ardından **kapsam** listesinden yeni bir dağıtım kapsamı seçin.

     **Web** değeri, ana sayfanın yalnızca projede belirtilen Web sitesi için geçerli olduğu anlamına gelir. **Site** değeri, ana sayfanın tüm alt siteleri ve kök Web 'i içeren geçerli site koleksiyonuna uygulandığı anlamına gelir. Diğer değerler uygulanmaz.

    > [!NOTE]
    > Temalar yalnızca site koleksiyonu düzeyine uygulanabileceğinden, bir temanın kapsamını **site**dışında bir şeyle ayarlamanıza gerek kalmaz. Bir tema alt sitede kullanılıyorsa hatalar oluşabilir.

12. Menü çubuğunda **yapı** > **dağıtım çözümü**' ni seçin.

13. Dosyaların doğru şekilde dağıtılıp dağıtılmadığını doğrulamak için SharePoint sitesini açın, **Site eylemleri** menüsünü seçin, **site ayarları** komutunu seçin ve ardından **ana sayfalar** bağlantısını ya da **Temalar** bağlantısını seçin.

     Ana sayfaların veya temaların listesi görüntülenir ve içeri aktardığınız ana sayfa ya da temayı içerir.

## <a name="see-also"></a>Ayrıca bkz.
- [Ana Sayfalar](/previous-versions/office/developer/sharepoint-2010/ms443795(v=office.14))
- [Mevcut bir SharePoint sitesinden öğeleri içeri aktarma](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)
- [SharePoint için sayfa oluşturma](../sharepoint/creating-pages-for-sharepoint.md)
- [Çözümdeki dosyaları dahil etmek için modülleri kullanma](../sharepoint/using-modules-to-include-files-in-the-solution.md)
