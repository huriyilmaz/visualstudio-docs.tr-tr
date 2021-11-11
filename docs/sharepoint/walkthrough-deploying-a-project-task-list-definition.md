---
title: 'izlenecek yol: Project Görev Listesi tanımını dağıtma | Microsoft Docs'
description: bu kılavuzda, proje görevlerini izlemek üzere bir SharePoint listesi oluşturmak, özelleştirmek, hatalarını ayıklamak ve dağıtmak için Visual Studio kullanın.
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
ms.openlocfilehash: 0fc1504118bdff670a59078c151c850aeebcaf1b
ms.sourcegitcommit: abfcccf63234819c75a61bf2c4c7f710a9d23cdb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/11/2021
ms.locfileid: "132250640"
---
# <a name="walkthrough-deploy-a-project-task-list-definition"></a>İzlenecek yol: proje görev listesi tanımını dağıtma

bu izlenecek yol, [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)] proje görevlerini izlemek üzere SharePoint listesi oluşturmak, özelleştirmek, hatalarını ayıklamak ve dağıtmak için nasıl kullanılacağını gösterir.

[!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Önkoşullar

- desteklenen Microsoft Windows sürümleri ve SharePoint.

- Visual Studio 2017 veya Azure DevOps Services.

## <a name="create-a-sharepoint-list"></a>SharePoint listesi oluşturma

SharePoint listesi projesi oluşturun ve liste tanımını görevlerle ilişkilendirin.

1. **yeni Project** iletişim kutusunu açın, **SharePoint** düğümünü genişletin ve ardından **2010** düğümünü seçin.

2. **şablonlar** bölmesinde **SharePoint 2010 Project** şablonunu seçin, projeyi **projecttasklist** olarak adlandırın ve **tamam** düğmesini seçin.

     **SharePoint özelleştirme sihirbazı** görüntülenir.

3. hata ayıklama için kullandığınız yerel SharePoint sitesini belirtin, **grup çözümü olarak dağıt** seçenek düğmesini seçin ve ardından **son** düğmesini seçin.

4. Proje için kısayol menüsünü açın ve ardından   >  **Yeni öğe** Ekle ' yi seçin.

5. **Şablonlar** bölmesinde, **liste** şablonunu seçin ve sonra **Ekle** düğmesini seçin.

     **SharePoint özelleştirme sihirbazı** görüntülenir.

6. **listenizde hangi adı göstermek istiyorsunuz?** kutusuna **Project Görev Listesi** girin.

7. **Var olan bir liste türüne göre özelleştirilemeyen olmayan bir liste oluştur** düğmesini seçin ve ardından listesinde **Görevler**' i seçin ve ardından **son** düğmesini seçin.

     Liste, özellik ve paket **Çözüm Gezgini** görüntülenir.

## <a name="add-an-event-receiver"></a>Olay alıcısı ekleme

Görev listesinde, görevin son tarihini ve açıklamasını otomatik olarak ayarlayan bir olay alıcısı ekleyebilirsiniz. Aşağıdaki yordam, liste örneğine bir olay alıcısı olarak basit bir olay işleyicisi ekler.

1. Proje düğümünün kısayol menüsünü açın, **Ekle**' yi ve ardından **Yeni öğe**' yi seçin.

2. SharePoint şablonları listesinde, **olay alıcısı** şablonunu seçin ve sonra **projecttasklisteventalıcısı** olarak adlandırın.

     **SharePoint özelleştirme sihirbazı** görüntülenir.

3. **olay alıcıyı seç Ayarlar** sayfasında, **ne tür olay alıcısı** seçin listesinde, olay alıcı türü olarak **liste öğe olayları** ' nı seçin.

4. **Hangi öğede olay kaynağı listesi olması gerekir** , **Görevler**' i seçin.

5. İşlenecek olaylar listesinde, **bir öğe eklendiği** yanındaki onay kutusunu işaretleyin ve ardından **son** düğmesini seçin.

     Projeye **Projecttasklisteventalıcısı** adlı bir kod dosyası ile yeni bir olay alıcısı düğümü eklenir.

6. `ItemAdded` **Projecttasklisteventalıcı** kod dosyasındaki yöntemine kod ekleyin. Her yeni görev eklendiğinde, göreve varsayılan bir bitiş tarihi ve açıklama eklenir. Varsayılan son tarih 1 Temmuz 2009 ' dir.

     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/projecttasklist1/projecttasklisteventreceiver/projecttasklisteventreceiver.vb" id="Snippet1":::
     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/projecttasklist/projecttasklisteventreceiver/projecttasklisteventreceiver.cs" id="Snippet1":::

## <a name="customize-the-project-task-list-feature"></a>Proje görev listesi özelliğini özelleştirme

SharePoint bir çözüm oluşturduğunuzda, Visual Studio otomatik olarak varsayılan proje öğeleri için özellikler oluşturur. SharePoint sitesinin proje görev listesi ayarlarını, özellik tasarımcısını kullanarak özelleştirebilirsiniz.

1. **Çözüm Gezgini**, **Özellikler**' i genişletin.

2. **Özellik1** için kısayol menüsünü açın ve **Tasarımcı görüntüle**' yi seçin.

3. **başlık** kutusuna **Project Görev Listesi özelliği** yazın.

4. **Kapsam** listesinden **Web**' i seçin.

5. **Özellikler** penceresinde, **Version** özelliği için değer olarak **1.0.0.0** girin.

## <a name="customize-the-project-task-list-package"></a>Proje görev listesi paketini özelleştirme

bir SharePoint projesi oluşturduğunuzda, Visual Studio varsayılan proje öğelerini içeren özellikleri otomatik olarak pakete ekler. SharePoint sitesinin proje görev listesi ayarlarını paket tasarımcısını kullanarak özelleştirebilirsiniz.

1. **SolutionExplorer**'Da, **paket** için kısayol menüsünü açın ve ardından **Görünüm Tasarımcısı**' nı seçin.

2. **Ad** kutusuna **ProjectTaskListPackage** yazın.

3. **Web sunucusunu Sıfırla** onay kutusunu seçin.

## <a name="build-and-test-the-project-task-list"></a>Proje görev listesini oluşturma ve test etme

projeyi çalıştırdığınızda SharePoint sitesi açılır. Ancak, görev listesinin konumuna el ile gitmeniz gerekir.

1. Proje Görev listenizi derlemek ve dağıtmak için **F5** tuşunu seçin.

     SharePoint site açılır.

2. **Giriş** sekmesini seçin.

3. sol kenar çubuğunda **Project Görev Listesi** bağlantısını seçin.

     Project Görev Listesi sayfası görüntülenir.

4. **Liste araçları** sekmesinde, **öğeler** sekmesini seçin.

5. **Öğeler** grubunda, **Yeni öğe** düğmesini seçin.

6. **Başlık** metin kutusuna **Task1** girin.

7. **Kaydet** düğmesini seçin.

     Site yenilendikten sonra, **Task1** görevi son tarih olan 7/1/2009 ile görüntülenir.

8. **Task1** seçin.

     Görevin ayrıntılı görünümü görüntülenir ve açıklama "Bu kritik bir görevdir." ifadesi gösterilir.

## <a name="deploy-the-project-task-list"></a>Proje görev listesini dağıtma

Proje görev listesini derleyip test ettikten sonra, *yerel sisteme* veya *uzak bir sisteme* dağıtabilirsiniz. Yerel sistem, çözümü geliştirmiş olduğunuz bilgisayardır, ancak uzak sistem farklı bir bilgisayardır.

### <a name="to-deploy-the-project-task-list-to-the-local-system"></a>Proje görev listesini yerel sisteme dağıtmak için

Visual Studio menü çubuğunda **Build**  >  **Deploy Solution**' ı seçin.

Visual Studio ııs uygulama havuzunu geri dönüştürür, çözümün var olan sürümlerini geri çeker, çözüm paketi (*. wsp*) dosyasını SharePoint kopyalar ve ardından özelliklerini etkinleştirir. Artık SharePoint çözümünü kullanabilirsiniz. dağıtım yapılandırma adımları hakkında daha fazla bilgi için bkz. [nasıl yapılır: SharePoint dağıtım yapılandırmasını düzenleme](../sharepoint/how-to-edit-a-sharepoint-deployment-configuration.md).

### <a name="to-deploy-the-project-task-list-to-a-remote-system"></a>Proje görev listesini uzak bir sisteme dağıtmak için

1. Visual Studio menü çubuğunda **derleme**  >  **yayımla**' yı seçin.

2. **Yayımla** Iletişim kutusunda **dosya sistemine yayınla** seçenek düğmesini seçin.

     **Yayımla** iletişim kutusundaki hedef konumunu üç nokta düğmesi ![üç nokta simgesini](../sharepoint/media/ellipsisicon.gif "Üç nokta simgesi") seçip başka bir konuma giderek değiştirebilirsiniz.

3. **Yayımla** düğmesini seçin.

     Çözüm için bir *. wsp* dosyası oluşturulur.

4. *. wsp* dosyasını uzak SharePoint sistemine kopyalayın.

5. `Add-SPUserSolution`paketi uzaktan SharePoint yüklemesine yüklemek için PowerShell komutunu kullanın. (Grup çözümleri için `Add-SPSolution` komutunu kullanın.)

     Örneğin, `Add-SPUserSolution C:\MyProjects\ProjectTaskList\ProjectTaskList\bin\Debug\ProjectTaskList.wsp`.

6. `Install-SPUserSolution`Çözümü dağıtmak Için PowerShell komutunu kullanın. (Grup çözümleri için `Install-SPSolution` komutunu kullanın.)

     Örneğin, `Install-SPUserSolution -Identity ProjectTaskList.wsp -Site http://NewSiteName`.

     uzaktan dağıtım hakkında daha fazla bilgi için, bkz. SharePoint 2010 ' de [çözümleri kullanma](/previous-versions/office/developer/sharepoint-2010/ee534972(v=office.14)) ve [PowerShell ile çözüm ekleme ve dağıtma](/powershell/module/sharepoint-server/install-spsolution?view=sharepoint-server-ps).

## <a name="next-steps"></a>Sonraki adımlar

aşağıdaki konulardan SharePoint çözümlerini özelleştirme ve dağıtma hakkında daha fazla bilgi edinebilirsiniz:

- [İzlenecek yol: SharePoint için bir site sütunu, içerik türü ve liste oluşturma](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md)

- [Nasıl yapılır: olay alıcısı oluşturma](../sharepoint/how-to-create-an-event-receiver.md)

- [SharePoint sunucusu 2010 Windows PowerShell](/powershell/module/sharepoint-server)

## <a name="see-also"></a>Ayrıca bkz.
[SharePoint çözümleri paketleme ve dağıtma](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
