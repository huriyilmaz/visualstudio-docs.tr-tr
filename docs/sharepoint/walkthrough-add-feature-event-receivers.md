---
title: 'İzlenecek yol: özellik Olay alıcıları ekleme | Microsoft Docs'
description: Bu izlenecek yolda, bir SharePoint özelliği yüklendiğinde, etkinleştirildiğinde, devre dışı bırakıldığında veya kaldırıldığında yürütülen Yöntemler olan özellik Olay alıcıları ekleyin.
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 98b85222fca4da6dfca653ad74e1315801798d83
ms.sourcegitcommit: 8e9c38da7bcfbe9a461c378083846714933a0e1e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/09/2020
ms.locfileid: "96915602"
---
# <a name="walkthrough-add-feature-event-receivers"></a>İzlenecek yol: özellik Olay alıcıları ekleme
Özellik Olay alıcıları, SharePoint 'te aşağıdaki özellikle ilgili olaylardan biri gerçekleştiğinde yürütülen yöntemlerdir:

- Bir özellik yüklendi.

- Bir özellik etkinleştirilir.

- Bir özellik devre dışı bırakıldı.

- Bir özellik kaldırılır.

Bu izlenecek yol, bir SharePoint projesindeki bir özelliğe olay alıcısının nasıl ekleneceğini gösterir. Aşağıdaki görevleri gösterir:

- Özellik olay alıcısı ile boş bir proje oluşturma.

- **Featuredevre dışı bırakma** yöntemi işleniyor.

- Duyurular listesine duyuru eklemek için SharePoint projesi nesne modelini kullanma.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Önkoşullar
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:

- Desteklenen Microsoft Windows ve SharePoint sürümleri.

- Visual Studio.

## <a name="create-a-feature-event-receiver-project"></a>Özellik olay alıcısı projesi oluşturma
 İlk olarak, özellik olay alıcısını içeren bir proje oluşturun.

#### <a name="to-create-a-project-with-a-feature-event-receiver"></a>Özellik olay alıcısı olan bir proje oluşturmak için

1. **File**  >  **New**  >  **Yeni proje** iletişim kutusunu göstermek için menü çubuğunda dosya yeni **Proje** ' yi seçin.

2. **Visual C#** veya **Visual Basic** altında **SharePoint** düğümünü genişletin ve ardından **2010** düğümünü seçin.

3. **Şablonlar** bölmesinde, **SharePoint 2010 proje** şablonunu seçin.

     Bu proje türünü, proje şablonu bulunmadığından özellik Olay alıcıları için kullanırsınız.

4. **Ad** kutusuna **FeatureEvtTest** girin ve ardından **Tamam** düğmesini seçerek **SharePoint Özelleştirme Sihirbazı**'nı görüntüleyin.

5. **Hata ayıklama için site ve güvenlik düzeyini belirtin** sayfasında, yeni özel alan öğesini eklemek istediğiniz SharePoint Server sitesinin URL 'sini girin veya varsayılan konumu (http:// \<*system name*> /) kullanın.

6. **Bu SharePoint çözümünün güven düzeyi nedir?** bölümünde, **Grup çözümü olarak dağıt** seçenek düğmesini seçin.

     Korumalı çözümler ve Grup çözümleri hakkında daha fazla bilgi için bkz. [Korumalı çözüm konuları](../sharepoint/sandboxed-solution-considerations.md).

7. **Son** düğmesini seçin ve ardından özellik1 adlı bir özelliğin **Özellikler** düğümü altında göründüğünü unutmayın.

## <a name="add-an-event-receiver-to-the-feature"></a>Özelliğe bir olay alıcısı ekleyin
 Sonra, özelliğe bir olay alıcısı ekleyin ve özellik devre dışı bırakıldığında yürütülen kodu ekleyin.

#### <a name="to-add-an-event-receiver-to-the-feature"></a>Özelliğe bir olay alıcısı eklemek için

1. Özellikler düğümü için kısayol menüsünü açın ve özellik oluşturmak için **Özellik Ekle** ' yi seçin.

2. **Özellikler** düğümü altında, **özellik1** için kısayol menüsünü açın ve sonra özelliğe bir olay alıcısı eklemek için **olay alıcısı Ekle** ' yi seçin.

     Bu, Özellik1 altına bir kod dosyası ekler. Bu durumda, projenizin geliştirme diline bağlı olarak *Feature1.EventReceiver.cs* veya *Özellik1. eventahize. vb* olarak adlandırılır.

3. Projeniz ' de yazılmışsa [!INCLUDE[csprcs](../sharepoint/includes/csprcs-md.md)] , şu kodu henüz yoksa olay alıcısının üst kısmına ekleyin:

     [!code-csharp[SP_FeatureEvt#1](../sharepoint/codesnippet/CSharp/featureevttest2/features/feature1/feature1.eventreceiver.cs#1)]

4. Olay alıcısı sınıfı, olay olarak davranan çeşitli açıklamalı yöntemler içerir. **Featuredevre dışı bırakma** yöntemini aşağıdaki kodla değiştirin:

     [!code-vb[SP_FeatureEvt#2](../sharepoint/codesnippet/VisualBasic/featureevt2vb/features/feature1/feature1.eventreceiver.vb#2)]
     [!code-csharp[SP_FeatureEvt#2](../sharepoint/codesnippet/CSharp/featureevttest2/features/feature1/feature1.eventreceiver.cs#2)]

## <a name="test-the-feature-event-receiver"></a>Özellik olay alıcısını test etme
 Sonra, özelliği **devre dışı bırak yönteminin SharePoint** Duyurular listesine bir duyuru çıkışı yapıp bırakmadığını test etmek için özelliği devre dışı bırakın.

#### <a name="to-test-the-feature-event-receiver"></a>Özellik olay alıcısını test etmek için

1. Projenin **etkin dağıtım yapılandırma** özelliğinin değerini **etkinleştirme yok** olarak ayarlayın.

     Bu özelliğin ayarlanması, özelliğin SharePoint 'te etkinleşmesini engeller ve özellik olay alıcılarından hata ayıklamanıza olanak tanır. Daha fazla bilgi için bkz. [SharePoint Çözümlerinde hata ayıklama](../sharepoint/debugging-sharepoint-solutions.md).

2. Projeyi çalıştırmak ve SharePoint 'e dağıtmak için **F5** tuşunu seçin.

3. SharePoint Web sayfasının en üstünde, **Site eylemleri** menüsünü açın ve ardından **site ayarları**' nı seçin.

4. **Site ayarları** sayfasının **Site eylemleri** bölümünde, **site özelliklerini yönet** bağlantısını seçin.

5. **Özellikler** sayfasında, **FeatureEvtTest Özellik1** özelliğinin yanındaki **Etkinleştir** düğmesini seçin.

6. **Özellikler** sayfasında, **FeatureEvtTest Özellik1** özelliğinin yanındaki **devre dışı bırak** düğmesini seçin ve sonra özelliği devre dışı bırakmak için **Bu özelliği devre dışı bırak** onay bağlantısını seçin.

7. **Giriş** düğmesini seçin.

     Özellik devre dışı bırakıldıktan sonra **Duyurular** listesinde bir duyuru göründüğünü unutmayın.

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: olay alıcısı oluşturma](../sharepoint/how-to-create-an-event-receiver.md)
- [SharePoint çözümleri geliştirme](../sharepoint/developing-sharepoint-solutions.md)