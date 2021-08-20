---
title: 'Nasıl: Ana Sayfayı veya Tema Sayfasını | Microsoft Docs'
description: SharePoint Designer'da ana sayfalar ve temalar için şablonları oluşturun, ardından Visual Studio sitenize tutarlı bir görünüm SharePoint sayfaları içeri aktarın.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, importing items
- importing items [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: 69d304d476be4b1e0ab97500b1f13b04bd68ff1f
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122093014"
---
# <a name="how-to-import-a-master-page-or-theme"></a>Nasıl olur: Ana sayfayı veya temayı içeri aktarma
  Ana sayfalar ve temalar oluşturarak SharePoint tutarlı bir görünüm elde edebilirsiniz. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]bu öğeler için şablonlar sağlamaz, ancak bunları SharePoint Designer'da oluşturabilir ve içine [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] aktarabilirsiniz. Daha fazla bilgi için Microsoft [web sitesinde Building Block: Pages Kullanıcı Arabirimi](/previous-versions/office/developer/sharepoint-2010/ee539040(v=office.14)) ve Kullanıcı Arabirimi makaleye bakın.

### <a name="to-import-a-master-page-or-theme"></a>Ana sayfayı veya temayı içeri aktarma

1. içinde [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] bir proje oluşturun veya SharePoint açın.

     Bir proje oluşturma hakkında bilgi SharePoint için [bkz. SharePoint proje ve proje öğesi şablonları.](../sharepoint/sharepoint-project-and-project-item-templates.md)

2. Menü çubuğunda Yeni Öğe **Ekle'Project**  >  **seçin.**

3. Yeni Öğe **Ekle iletişim** kutusunda, SharePoint **düğümünü** genişletin ve **ardından 2010 düğümünü** seçin.

4. Modül şablonları SharePoint modül şablonunu **seçin** ve ardından modül için bir ad belirtin.

     Modül, dağıtım sırasında belirttiğiniz bir konuma dağıtım için dosyalar (ana sayfa veya tema dosyaları gibi) SharePoint.

5. Modülde,Sample.txtadlı varsayılan *Sample.txt.*

6. Modül düğümünü seçin.

7. Menü çubuğunda Var Olan Öğe  >  **Project'ı ve** ardından ana sayfayı veya tema dosyasını seçin.

     Ana sayfa dosyalarının bir .master uzantısı ve tema dosyalarının .thmx uzantısı vardır.

8. Bir ana sayfa eklediyseniz, **modülün özelliklerinde** Dağıtım **ÇakışmaSı** Çözümleme ayarını Otomatik olarak değiştirin.

    > [!NOTE]
    > Ana sayfanın adı Varsayılan Ana Sayfa veya Özel Ana Sayfa olarak işaretlenmiş mevcut bir ana sayfanın adıyla aynı olduğunda hatalar oluşabilir. Bu sorunun nasıl çözülecekleri hakkında bilgi için bkz. Adım adım: Özel bir ana sayfayı ve site sayfasını [görüntüsüyle içeri aktarma.](../sharepoint/walkthrough-import-a-custom-master-page-and-site-page-with-an-image.md)

9. Modülde, *Elements.xml.*

     Bu dosyanın *Elements.xml* ana sayfaya veya temaya başvurarak güncelleştirmeniz gerekir.

10. Ana sayfa için mevcut modül işaretlemesini aşağıdaki işaretlemeyle değiştirin.

    ```xml
    <Module Name="[Module Name]" Url="_catalogs/masterpage">
        <File Path="[Module Name]\[Master Page Name].master"
          Url="[Master Page Name].master" Type="GhostableInLibrary" />
    </Module>
    ```

     Bir tema için mevcut modül işaretlemesini aşağıdaki işaretlemeyle değiştirin.

    ```xml
    <Module Name="[Module Name]" Url="_catalogs/theme"
        <File Path="[Module Name]\[Theme Name].thmx" Url="[Theme
          Name].thmx" Type="GhostableInLibrary" />
    </Module>
    ```

     Yer tutucu değerlerini modülün gerçek adları ve ana sayfa veya tema ile değiştirebilirsiniz.

     özniteliği `Type="GhostableInLibrary"` öğenin içerik veritabanına ekli olduğunu gösterir ve modülün özniteliği, dosyanın içerik veritabanında `Url` nereye SharePoint belirtir.

11. Ana sayfanın dağıtım kapsamını değiştirmek için, **Çözüm Gezgini** sayfasında özellik dosyasını Özellik Tasarımcısı'nda açın ve Kapsam listesinden yeni bir dağıtım **kapsamı** seçin.

     **Web değeri,** ana sayfanın yalnızca projede belirtilen web sitesi için geçerli olduğu anlamına gelir. **Site değeri,** ana sayfanın tüm alt siteleri ve kök web'i içeren geçerli site koleksiyonu için geçerli olduğu anlamına gelir. Diğer değerler geçerli değildir.

    > [!NOTE]
    > Temalar yalnızca site koleksiyonu düzeyi için geçerli olduğundan, bir temanın kapsamını Site dışında bir şey olarak ayarlamamanizi **öneririz.** Bir tema bir alt sitede kullanılıyorsa hatalar oluşabilir.

12. Menü çubuğunda Çözümü **Dağıtın'ı**  >  **seçin.**

13. Dosyaların doğru dağıtıldığından emin olmak için SharePoint sitesini açın, **Site** Eylemleri menüsünü seçin, **Site** Ayarlar komutunu seçin ve  ardından Ana Sayfalar bağlantısını veya Temalar bağlantısını **seçin.**

     Ana sayfaların veya temaların listesi görünür ve ana sayfayı veya içe aktarılmış temayı içerir.

## <a name="see-also"></a>Ayrıca bkz.
- [Ana Sayfalar](/previous-versions/office/developer/sharepoint-2010/ms443795(v=office.14))
- [Mevcut bir siteden öğeleri SharePoint alma](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)
- [SharePoint için sayfalar oluşturma](../sharepoint/creating-pages-for-sharepoint.md)
- [Çözüme dosya eklemek için modülleri kullanma](../sharepoint/using-modules-to-include-files-in-the-solution.md)
