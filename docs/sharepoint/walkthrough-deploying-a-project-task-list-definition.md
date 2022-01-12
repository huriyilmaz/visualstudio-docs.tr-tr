---
title: 'adım adım kılavuz: Project Görev Listesi Tanımı | Microsoft Docs'
description: Bu kılavuzda, proje Visual Studio bir liste oluşturmak, özelleştirmek, hata ayıklamak ve dağıtmak için SharePoint'leri kullanın.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, deploying
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: d49e8bb4b657c3185693788c8e8c313cf39e43fe
ms.sourcegitcommit: dcecc0ed37b5e976b5dc83c5128ba5ecc8bc04b1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/04/2022
ms.locfileid: "135750492"
---
# <a name="walkthrough-deploy-a-project-task-list-definition"></a>Adım adım kılavuz: Proje görev listesi tanımını dağıtma

Bu kılavuzda, proje görevlerini izlemek üzere bir uygulama listesi [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)] oluşturmak, özelleştirmek, hata ayıklamak ve SharePoint için nasıl kullanabileceğiniz anlatımlır.

[!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Önkoşullar

- Microsoft Windows ve SharePoint.

- Visual Studio 2017 veya Azure DevOps Services.

## <a name="create-a-sharepoint-list"></a>Bir SharePoint oluşturma

Bir SharePoint listesi projesi oluşturun ve liste tanımını görevlerle ilişkilendirme.

1. Yeni **Project** iletişim kutusunu açın, **SharePoint** düğümünü genişletin ve ardından **2010 düğümünü** seçin.

2. Şablonlar **bölmesinde,** **SharePoint 2010 Project** şablonunu seçin, **projeye ProjectTaskList** adını ve ardından Tamam **düğmesini** seçin.

     SharePoint **Özelleştirme Sihirbazı** görüntülenir.

3. Hata ayıklama için SharePoint yerel uygulama sitesini belirtin, Grup çözümü olarak dağıt **seçeneğini** belirleyin ve ardından Son **düğmesini** seçin.

4. Projenin kısayol menüsünü açın ve Yeni Öğe **Ekle'yi**  >  **seçin.**

5. Şablonlar **bölmesinde** Liste şablonunu **ve** ardından Ekle **düğmesini** seçin.

     SharePoint **Özelleştirme Sihirbazı** görüntülenir.

6. Listeniz **için hangi adı görüntülemek istiyorsunuz?** kutusuna Project Görev Listesi. 

7. Mevcut **liste türü seçeneğine** göre özelleştirilebilir olmayan bir liste oluştur düğmesini seçin ve ardından listesinde Görevler 'i ve ardından Son **düğmesini** seçin.

     Liste, özellik ve paket, **Çözüm Gezgini.**

## <a name="add-an-event-receiver"></a>Olay alıcısı ekleme

Görev listesinde, görevin son tarihini ve açıklamasını otomatik olarak ayaran bir olay alıcısı ekleyebilirsiniz. Aşağıdaki yordam, liste örneğine olay alıcısı olarak basit bir olay işleyicisi ekler.

1. Proje düğümünün kısayol menüsünü açın, **Ekle'yi ve ardından** Yeni **Öğe'yi seçin.**

2. Uygulama şablonları listesinde SharePoint Alıcısı şablonunu  seçin ve **projectTaskListEventReceiver olarak ad girin.**

     SharePoint **Özelleştirme Sihirbazı** görüntülenir.

3. Olay **Alıcısı Seç Ayarlar,** Olay **alıcısı** türü olarak Hangi olay alıcısı istediğiniz listesinde Öğe **Olaylarını Listele'yi** seçin.

4. Olay **kaynağı olması gereken öğe listesinde Görevler'i** **seçin.**

5. İşlenecek olaylar listesinde Öğe eklendi seçeneğinin yanındaki onay kutusunu **işaretleyin** ve ardından Son **düğmesini** seçin.

     Projeye **ProjectTaskListEventReceiver** adlı bir kod dosyasıyla yeni bir olay alıcı düğümü eklenir.

6. `ItemAdded` **ProjectTaskListEventReceiver kod dosyasındaki yöntemine kod** ekleyin. Her yeni görev ekleniyorsa, varsayılan bir son tarih ve göreve bir açıklama eklenir. Varsayılan son tarih 1 Temmuz 2009'dır.

     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/projecttasklist1/projecttasklisteventreceiver/projecttasklisteventreceiver.vb" id="Snippet1":::
     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/projecttasklist/projecttasklisteventreceiver/projecttasklisteventreceiver.cs" id="Snippet1":::

## <a name="customize-the-project-task-list-feature"></a>Proje görev listesi özelliğini özelleştirme

Yeni bir çözüm SharePoint, Visual Studio proje öğeleri için otomatik olarak özellikler oluşturur. Özellik Tasarımcısı'SharePoint sitenin proje görev listesi ayarlarını özelleştirebilirsiniz.

1. Bu **Çözüm Gezgini** Özellikler'i **genişletin.**

2. **Özellik1** için kısayol menüsünü açın ve ardından **Görünüm Tasarımcısı.**

3. Başlık **kutusuna** Özellik Project Görev Listesi **girin.**

4. Kapsam **listesinde Web'i** **seçin.**

5. Özellikler **penceresinde** Sürüm özelliğinin **değeri olarak 1.0.0.0** **girin.**

## <a name="customize-the-project-task-list-package"></a>Proje görev listesi paketini özelleştirme

Bir proje SharePoint, Visual Studio varsayılan proje öğelerini içeren özellikleri otomatik olarak pakete ekler. Paket Tasarımcısı'SharePoint sitenin proje görev listesi ayarlarını özelleştirebilirsiniz.

1. **SolutionExplorer'da** Paket kısayol menüsünü **açın** ve ardından **Paket'Görünüm Tasarımcısı.**

2. Ad **kutusuna** **ProjectTaskListPackage yazın.**

3. Web Sunucusunu **Sıfırla onay** kutusunu seçin.

## <a name="build-and-test-the-project-task-list"></a>Proje görev listesini derleme ve test

Projeyi çalıştırdıktan sonra SharePoint açılır. Ancak, görev listesinin bulunduğu konuma el ile gitmelisiniz.

1. Proje görev listenizi oluşturmak ve dağıtmak için **F5** anahtarını seçin.

     SharePoint sitesi açılır.

2. Giriş **sekmesini** seçin.

3. Sol kenar çubuğuna Tıklayın bağlantısını **Project Görev Listesi** seçin.

     Project Görev Listesi sayfası görüntülenir.

4. Liste **Araçları sekmesinde** Öğeler **sekmesini** seçin.

5. Öğeler **grubunda** Yeni Öğe **düğmesini** seçin.

6. Başlık **metin kutusuna** **Task1 girin.**

7. Kaydet **düğmesini** seçin.

     Site yenilendikten sonra **Task1** görevi son tarihi 1/7/2009 olarak görünür.

8. **Görev1'i seçin.**

     Görevin ayrıntılı görünümü görüntülenir ve açıklama "Bu kritik bir görevdir" ifadesini gösterir.

## <a name="deploy-the-project-task-list"></a>Proje görev listesini dağıtma

Proje görev listesini derleme ve test sonrasında yerel sisteme veya uzak *bir sisteme* *dağıtabilirsiniz.* Yerel sistem, çözümü geliştirdiğiniz bilgisayarla aynı, uzak sistem ise farklı bir bilgisayardır.

### <a name="to-deploy-the-project-task-list-to-the-local-system"></a>Proje görev listesini yerel sisteme dağıtmak için

Uygulama menü Visual Studio Çözümü **Derleme'yi**  >  **seçin.**

Visual Studio IIS uygulama havuzunu geri dönüştürer, çözümün mevcut sürümlerini geri çekin, çözüm paketi (*.wsp*) dosyasını SharePoint dosyasına kopyalar ve ardından özelliklerini etkinleştirir. Artık çözümü SharePoint. Dağıtım yapılandırma adımları hakkında daha fazla bilgi için [bkz. Nasıl: SharePoint yapılandırmayı düzenleme.](../sharepoint/how-to-edit-a-sharepoint-deployment-configuration.md)

### <a name="to-deploy-the-project-task-list-to-a-remote-system"></a>Proje görev listesini uzak bir sisteme dağıtmak için

1. Yayımlama menü Visual Studio Yayımla'yı   >  **seçin.**

2. Yayımla **iletişim** kutusunda Dosya Sisteminde **Yayımla seçeneğini** belirleyin.

     Üç nokta düğmesini Üç Nokta **Simgesi seçerek** ve ardından ![](../sharepoint/media/ellipsisicon.gif "Üç Nokta Simgesi") başka bir konuma giderek Yayımla iletişim kutusunda hedef konumu değiştirebilirsiniz.

3. Yayımla **düğmesini** seçin.

     Çözüm için bir *.wsp* dosyası oluşturulur.

4. *.wsp dosyasını* uzak SharePoint kopyalayın.

5. Paketi uzak sunucu yüklemesinde yüklemek için PowerShell `Add-SPUserSolution` SharePoint kullanın. (Grup çözümleri için komutunu `Add-SPSolution` kullanın.)

     Örneğin, `Add-SPUserSolution C:\MyProjects\ProjectTaskList\ProjectTaskList\bin\Debug\ProjectTaskList.wsp`.

6. Çözümü dağıtmak için PowerShell `Install-SPUserSolution` komutunu kullanın. (Grup çözümleri için komutunu `Install-SPSolution` kullanın.)

     Örneğin, `Install-SPUserSolution -Identity ProjectTaskList.wsp -Site http://NewSiteName`.

     Uzaktan dağıtım hakkında daha fazla bilgi için, [bkz. Using Solutions](/previous-versions/office/developer/sharepoint-2010/ee534972(v=office.14)) and [Adding and Deploying Solutions with PowerShell in SharePoint 2010](/powershell/module/sharepoint-server/install-spsolution?view=sharepoint-server-ps&preserve-view=true).

## <a name="next-steps"></a>Sonraki adımlar

Aşağıdaki konulardan uygulama çözümlerinin nasıl özelleştirebileceğiniz ve SharePoint daha fazla bilgi öğrenebilirsiniz:

- [Adım adım kılavuz: Site sütunu, içerik türü ve liste oluşturma SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md)

- [Nasıl: Olay alıcısı oluşturma](../sharepoint/how-to-create-an-event-receiver.md)

- [Windows PowerShell Server 2010 için SharePoint](/powershell/module/sharepoint-server)

## <a name="see-also"></a>Ayrıca bkz.
[Dağıtım çözümlerini SharePoint dağıtma](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
