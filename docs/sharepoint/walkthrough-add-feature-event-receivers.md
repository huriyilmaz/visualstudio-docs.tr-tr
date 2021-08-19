---
title: 'İzlenecek yol: özellik Olay alıcıları ekleme | Microsoft Docs'
description: bu izlenecek yolda, bir SharePoint özelliği yüklendiğinde, etkinleştirildiğinde, devre dışı bırakıldığında veya kaldırıldığında yürütülen yöntemler olan özellik olay alıcıları ekleyin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, advanced packaging tools
- SharePoint development in Visual Studio, event receivers
- SharePoint development in Visual Studio, feature event receivers
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: 58e4210244c09271741a89e2343bfaf06a6d2c20
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122084005"
---
# <a name="walkthrough-add-feature-event-receivers"></a>İzlenecek yol: özellik Olay alıcıları ekleme
Özellik Olay alıcıları SharePoint ' de aşağıdaki özellikle ilgili olaylardan biri gerçekleştiğinde yürütülen yöntemlerdir:

- Bir özellik yüklendi.

- Bir özellik etkinleştirilir.

- Bir özellik devre dışı bırakıldı.

- Bir özellik kaldırılır.

bu izlenecek yol, bir SharePoint projesindeki bir özelliğe olay alıcısının nasıl ekleneceğini gösterir. Aşağıdaki görevleri gösterir:

- Özellik olay alıcısı ile boş bir proje oluşturma.

- **Featuredevre dışı bırakma** yöntemi işleniyor.

- duyurular listesine bir duyuru eklemek için SharePoint projesi nesne modelini kullanma.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Önkoşullar
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:

- desteklenen Microsoft Windows sürümleri ve SharePoint.

- Visual Studio.

## <a name="create-a-feature-event-receiver-project"></a>Özellik olay alıcısı projesi oluşturma
 İlk olarak, özellik olay alıcısını içeren bir proje oluşturun.

#### <a name="to-create-a-project-with-a-feature-event-receiver"></a>Özellik olay alıcısı olan bir proje oluşturmak için

1.   >    >  **yeni Project** iletişim kutusunu göstermek için menü çubuğunda dosya yeni **Project** öğesini seçin.

2. **Visual C#** veya **Visual Basic** altındaki **SharePoint** düğümünü genişletin ve ardından **2010** düğümünü seçin.

3. **şablonlar** bölmesinde **SharePoint 2010 Project** şablonunu seçin.

     Bu proje türünü, proje şablonu bulunmadığından özellik Olay alıcıları için kullanırsınız.

4. **ad** kutusuna **featureevttest** yazın ve ardından **SharePoint özelleştirme sihirbazını** göstermek için **tamam** düğmesini seçin.

5. **hata ayıklama için site ve güvenlik düzeyini belirtin** sayfasında, yeni özel alan öğesini eklemek istediğiniz SharePoint sunucusu sitesinin URL 'sini girin veya varsayılan konumu (http:// \<*system name*> /) kullanın.

6. **bu SharePoint çözümü için güven düzeyi nedir?** bölümünde, **grup çözümü olarak dağıt** seçenek düğmesini seçin.

     Korumalı çözümler ve Grup çözümleri hakkında daha fazla bilgi için bkz. [Korumalı çözüm konuları](../sharepoint/sandboxed-solution-considerations.md).

7. **Son** düğmesini seçin ve ardından özellik1 adlı bir özelliğin **Özellikler** düğümü altında göründüğünü unutmayın.

## <a name="add-an-event-receiver-to-the-feature"></a>Özelliğe bir olay alıcısı ekleyin
 Sonra, özelliğe bir olay alıcısı ekleyin ve özellik devre dışı bırakıldığında yürütülen kodu ekleyin.

#### <a name="to-add-an-event-receiver-to-the-feature"></a>Özelliğe bir olay alıcısı eklemek için

1. Özellikler düğümü için kısayol menüsünü açın ve özellik oluşturmak için **Özellik Ekle** ' yi seçin.

2. **Özellikler** düğümü altında, **özellik1** için kısayol menüsünü açın ve sonra özelliğe bir olay alıcısı eklemek için **olay alıcısı Ekle** ' yi seçin.

     Bu, Özellik1 altına bir kod dosyası ekler. Bu durumda, projenizin geliştirme diline bağlı olarak *özellik1. Eventalıcı. cs* veya *Özellik1. eventahize. vb* olarak adlandırılır.

3. Projeniz ' de yazılmışsa [!INCLUDE[csprcs](../sharepoint/includes/csprcs-md.md)] , şu kodu henüz yoksa olay alıcısının üst kısmına ekleyin:

     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/featureevttest2/features/feature1/feature1.eventreceiver.cs" id="Snippet1":::

4. Olay alıcısı sınıfı, olay olarak davranan çeşitli açıklamalı yöntemler içerir. **Featuredevre dışı bırakma** yöntemini aşağıdaki kodla değiştirin:

     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/featureevt2vb/features/feature1/feature1.eventreceiver.vb" id="Snippet2":::
     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/featureevttest2/features/feature1/feature1.eventreceiver.cs" id="Snippet2":::

## <a name="test-the-feature-event-receiver"></a>Özellik olay alıcısını test etme
 sonra, özelliği devre dışı **bırakma** yönteminin SharePoint duyurular listesine bir duyuru çıkışı yapıp kullanmadığını test etmek için özelliği devre dışı bırakın.

#### <a name="to-test-the-feature-event-receiver"></a>Özellik olay alıcısını test etmek için

1. Projenin **etkin dağıtım yapılandırma** özelliğinin değerini **etkinleştirme yok** olarak ayarlayın.

     bu özellik ayarlandığında özelliğin SharePoint ' de etkinleştirilmesi önlenir ve özellik olay alıcılarından hata ayıklamanıza izin verir. daha fazla bilgi için bkz. [SharePoint çözümlerinde hata ayıklama](../sharepoint/debugging-sharepoint-solutions.md).

2. Projeyi çalıştırmak ve SharePoint dağıtmak için **F5** tuşunu seçin.

3. SharePoint Web sayfasının en üstünde, **site eylemleri** menüsünü açın ve ardından **site Ayarlar**' nı seçin.

4. **site Ayarlar** sayfasının **site eylemleri** bölümünde, **site özelliklerini yönet** bağlantısını seçin.

5. **Özellikler** sayfasında, **FeatureEvtTest Özellik1** özelliğinin yanındaki **Etkinleştir** düğmesini seçin.

6. **Özellikler** sayfasında, **FeatureEvtTest Özellik1** özelliğinin yanındaki **devre dışı bırak** düğmesini seçin ve sonra özelliği devre dışı bırakmak için **Bu özelliği devre dışı bırak** onay bağlantısını seçin.

7. **Giriş** düğmesini seçin.

     Özellik devre dışı bırakıldıktan sonra **Duyurular** listesinde bir duyuru göründüğünü unutmayın.

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: olay alıcısı oluşturma](../sharepoint/how-to-create-an-event-receiver.md)
- [SharePoint çözümleri geliştirme](../sharepoint/developing-sharepoint-solutions.md)