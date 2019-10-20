---
title: Eski durum makinesi kullanılıyor İş Akışı Tasarımcısı | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- StateFinalizationActivity activity
- StateActivity activity
- SetStateActivity activity
- EventDrivenActivity activity
- state machine workflow designer
- state machine workflows, designer
- state machine workflows, activities
- StateInitializationActivity activity
ms.assetid: 2cd21123-35c2-4eaf-82f6-86fce7a8f04d
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 8c2b1ce1f1b2c6a16b5576880904feadf37a3e7b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72606765"
---
# <a name="using-the-legacy-state-machine-workflow-designer"></a>Eski Durum Makinesi İş Akışı Tasarımcısını Kullanma
@No__t_0 içinde [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] veya [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)] hedefleyen yeni bir durum makinesi iş akışı projesi oluştururken, **durum makinesi Iş akışı konsol uygulamasını** ya da **durum makinesi iş akışı kitaplığı** eski ' ni kullanmayı seçebilirsiniz Proje şablonu. Bu durum makinesi proje şablonlarından birini seçerseniz, durum makinesi Tasarımcısı eski iş akışı Tasarımcısı Kullanıcı arabirimi olarak sunulur. Eski durum makinesi proje şablonları hakkında daha fazla bilgi için bkz. [nasıl yapılır: durum makinesi Iş akışı konsol uygulamaları (eski)](../workflow-designer/how-to-create-state-machine-workflow-console-applications-legacy.md) ve [nasıl yapılır: durum makinesi Iş akışı kitaplığı oluşturma (eski)](../workflow-designer/how-to-create-a-state-machine-workflow-library-legacy.md).

 Bir durum makinesi iş akışı, bir durumlar kümesinden oluşur. Bir durum, ilk durum olarak gösterilir. Her durum, belirli bir olay kümesini alabilir. Bir olaya bağlı olarak, başka bir duruma geçiş yapılabilir. Durum makinesi iş akışı son bir duruma sahip olabilir. Son duruma bir geçiş yapıldığında iş akışı sonlanır.

## <a name="state-machine-designer-views"></a>Durum makinesi tasarımcı görünümleri
 Durum makinesi Tasarımcısı bir serbest biçim tasarlayıcıdır, bu da etkinliklerin tasarım yüzeyinde serbestçe taşınabileceği anlamına gelir. Durum makinesi tasarımcısının iki görünümü vardır: *durum* görünümü ve *olay temelli* görünüm.

 Durum görünümü, durum etkinliklerini ve bir durum etkinliği içinde yer alan olay odaklı etkinlikleri gösterir. Bu görünümde, bir durumdan diğerine yapılan geçişler, olay odaklı etkinlikten başka bir duruma genişleyen satırlarla temsil edilir. Ayrıca, çizgiyi kendiniz çizerek geçişler de oluşturabilirsiniz. Geçişi çizmek için olay odaklı etkinliği seçin ve sonra etkinlikteki tutamaçlardan birini seçip sürükleyin. Bu eylem bir çizgi çizer. Bu satır daha sonra durumlar arasında bir geçiş belirten hedef durumuna eklenir.

 Olay temelli görünüme erişmek için olay temelli bir etkinliğe çift tıklayın. Görüntülenen tasarımcı, sıralı iş akışı tasarımcısına çok benzer. Tasarımcı 'nın en üstünde, bir gezinti çubuğu görüntülenen olay odaklı etkinliğe kadar etkinliklerin hiyerarşisini gösterir. Görüntülenecek hiyerarşideki herhangi bir öğeye tıklayarak durum görünümüne geri gidebilirsiniz. Durum görünümünde bir durumdan diğerine geçiş çizmiş ve bu etkinliğin olay odaklı görünümünü görüntülüyorsanız, sizin için olay odaklı etkinliğe bir küme durumu etkinliği eklenir. Durum ayarla etkinliğinin özelliklerini değiştirirseniz, durum görünümüne geri yansıtılır.

## <a name="state-machine-workflow-activities"></a>Durum makinesi Iş akışı etkinlikleri
 Aşağıdaki tabloda, bir durum makinesi iş akışı tasarımcısında kullanılan önemli etkinlikler açıklanmaktadır.

|Araç kutusu adı|Etkinlik|Açıklama|
|------------------|--------------|-----------------|
|**State**|[StateActivity](http://go.microsoft.com/fwlink?LinkID=65042)|Durum makinesindeki bir durumu temsil eder; , ek **StateActivity** etkinlikleri içerebilir. Daha fazla bilgi için bkz. [StateActivity etkinliğini kullanma](http://go.microsoft.com/fwlink?LinkID=65083).|
|**SetState**|[SetStateActivity](http://go.microsoft.com/fwlink?LinkID=65041)|Yeni bir duruma geçiş belirtir. Daha fazla bilgi için bkz. [SetStateActivity etkinliğini kullanma](http://go.microsoft.com/fwlink?LinkID=65082).|
|**StateInitialization**|[StateInitializationActivity](http://go.microsoft.com/fwlink?LinkID=65044)|Bir durum girildiğinde yürütülür; , diğer etkinlikleri içerebilir. Daha fazla bilgi için bkz. [StateInitialization etkinliğini kullanma](http://go.microsoft.com/fwlink?LinkID=65006).|
|**Statesonlandırılması**|[StateFinalizationActivity](http://go.microsoft.com/fwlink?LinkID=65043)|[StateActivity](http://go.microsoft.com/fwlink?LinkID=65042) etkinliğinden çıkarken içerilen etkinlikleri yürütür. Daha fazla bilgi için bkz. [StateFinalizationActivity etkinliğini kullanma](http://go.microsoft.com/fwlink?LinkID=65008).|
|**Olaytemelli**|[EventDrivenActivity](http://go.microsoft.com/fwlink?LinkID=65029)|Yürütmeye başlamak için bir dış olaya güvenen durumlar için kullanılır. **EventDrivenActivity** etkinliğinin ilk alt etkinlik olarak [IEventActivity](http://go.microsoft.com/fwlink?LinkID=65032) arabirimini uygulayan bir etkinliği olmalıdır. Daha fazla bilgi için bkz. [EventDrivenActivity etkinliğini kullanma](http://go.microsoft.com/fwlink?LinkID=65068).|

 Bir durum makinesi iş akışındaki ana bileşen [StateActivity](http://go.microsoft.com/fwlink?LinkID=65042) etkinliğidir. Olaylar bir durum makinesi iş akışındaki çeşitli noktalarda yakalandığından, olaylarla ilişkili görevleri işlemek için farklı durumlar girilir. İş akışı ömrü boyunca iş akışı bırakabilir ve birkaç farklı durum girebilir. Bu durumlar [SetStateActivity](http://go.microsoft.com/fwlink?LinkID=65041) etkinliğini kullanarak birbirlerine bağlanır.

 İş akışı tasarım yüzeyine yeni bir **StateActivity** sürüklediğinizde, şu şekilde [EventDrivenActivity](http://go.microsoft.com/fwlink?LinkID=65029), [StateInitializationActivity](http://go.microsoft.com/fwlink?LinkID=65044), [StateFinalizationActivity](http://go.microsoft.com/fwlink?LinkID=65043)veya ek **StateActivity** etkinlikleri ekleyebilirsiniz alt etkinlikler.

> [!CAUTION]
> İş akışları oluşturmak için durum makinesi iş akışı tasarımcısını kullandığınızda, **Belge anahat** görünümü penceresi ile tasarlamakta olduğunuz iş akışının yapısını izlemeniz gerekir. **Belge anahat** görünümü penceresinde durum makinesi iş akışı yapısının görünümü, iş akışı işaretleme dosyasındaki etkinliklerin mantıksal yerleşimini yansıtır. İş akışı etkinliklerinin tasarım yüzeyinde göründükleri fiziksel düzeni, iş akışı işaretleme dosyasındaki etkinliklerin mantıksal yerleşimini yansıtmayabilir.
>
> **Belge Anahattı** penceresini açmak Için, **Görünüm** menüsünde **diğer pencereler**' in üzerine gelin ve **Belge Anahattı**' nı seçin.

## <a name="see-also"></a>Ayrıca Bkz.
 [Nasıl yapılır: durum makinesi Iş akışı konsol uygulamaları oluşturma (eski)](../workflow-designer/how-to-create-state-machine-workflow-console-applications-legacy.md) nasıl yapılır: ' i kullanarak [StateActivity etkinliğini kullanarak](http://go.microsoft.com/fwlink?LinkID=65083) [durum makinesi iş akışı kitaplığı (eski)](../workflow-designer/how-to-create-a-state-machine-workflow-library-legacy.md) [durum makinesi iş akışları](http://go.microsoft.com/fwlink?LinkID=65016) oluşturma [ ](http://go.microsoft.com/fwlink?LinkID=65006) [, EventDrivenActivity etkinliğini kullanarak](http://go.microsoft.com/fwlink?LinkID=65068) [SetStateActivity etkinliğini kullanarak](http://go.microsoft.com/fwlink?LinkID=65082) [StateFinalizationActivity etkinliğini kullanan](http://go.microsoft.com/fwlink?LinkID=65008) StateInitializationActivity etkinliği