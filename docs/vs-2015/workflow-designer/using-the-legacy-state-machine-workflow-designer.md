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
ms.openlocfilehash: 77bb2c7abb49dbf6fe973ebc80f8340000e4afbd
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/10/2020
ms.locfileid: "75846001"
---
# <a name="using-the-legacy-state-machine-workflow-designer"></a>Eski Durum Makinesi İş Akışı Tasarımcısını Kullanma
[!INCLUDE[vs2010](../includes/vs2010-md.md)] içinde [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] veya [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)]hedefleyen yeni bir durum makinesi iş akışı projesi oluştururken, **durum makinesi Iş akışı konsol uygulamasını** veya **durum makinesi iş akışı kitaplığı** eski proje şablonunu kullanmayı seçebilirsiniz. Bu durum makinesi proje şablonlarından birini seçerseniz, durum makinesi Tasarımcısı eski iş akışı Tasarımcısı Kullanıcı arabirimi olarak sunulur. Eski durum makinesi proje şablonları hakkında daha fazla bilgi için bkz. [nasıl yapılır: durum makinesi Iş akışı konsol uygulamaları (eski)](../workflow-designer/how-to-create-state-machine-workflow-console-applications-legacy.md) ve [nasıl yapılır: durum makinesi Iş akışı kitaplığı oluşturma (eski)](../workflow-designer/how-to-create-a-state-machine-workflow-library-legacy.md).

 Bir durum makinesi iş akışı, bir durumlar kümesinden oluşur. Bir durum, ilk durum olarak gösterilir. Her durum, belirli bir olay kümesini alabilir. Bir olaya bağlı olarak, başka bir duruma geçiş yapılabilir. Durum makinesi iş akışı son bir duruma sahip olabilir. Son duruma bir geçiş yapıldığında iş akışı sonlanır.

## <a name="state-machine-designer-views"></a>Durum makinesi tasarımcı görünümleri
 Durum makinesi Tasarımcısı bir serbest biçim tasarlayıcıdır, bu da etkinliklerin tasarım yüzeyinde serbestçe taşınabileceği anlamına gelir. Durum makinesi tasarımcısının iki görünümü vardır: *durum* görünümü ve *olay temelli* görünüm.

 Durum görünümü, durum etkinliklerini ve bir durum etkinliği içinde yer alan olay odaklı etkinlikleri gösterir. Bu görünümde, bir durumdan diğerine yapılan geçişler, olay odaklı etkinlikten başka bir duruma genişleyen satırlarla temsil edilir. Ayrıca, çizgiyi kendiniz çizerek geçişler de oluşturabilirsiniz. Geçişi çizmek için olay odaklı etkinliği seçin ve sonra etkinlikteki tutamaçlardan birini seçip sürükleyin. Bu eylem bir çizgi çizer. Bu satır daha sonra durumlar arasında bir geçiş belirten hedef durumuna eklenir.

 Olay temelli görünüme erişmek için olay temelli bir etkinliğe çift tıklayın. Görüntülenen tasarımcı, sıralı iş akışı tasarımcısına çok benzer. Tasarımcı 'nın en üstünde, bir gezinti çubuğu görüntülenen olay odaklı etkinliğe kadar etkinliklerin hiyerarşisini gösterir. Görüntülenecek hiyerarşideki herhangi bir öğeye tıklayarak durum görünümüne geri gidebilirsiniz. Durum görünümünde bir durumdan diğerine geçiş çizmiş ve bu etkinliğin olay odaklı görünümünü görüntülüyorsanız, sizin için olay odaklı etkinliğe bir küme durumu etkinliği eklenir. Durum ayarla etkinliğinin özelliklerini değiştirirseniz, durum görünümüne geri yansıtılır.

## <a name="state-machine-workflow-activities"></a>Durum makinesi Iş akışı etkinlikleri
 Aşağıdaki tabloda, bir durum makinesi iş akışı tasarımcısında kullanılan önemli etkinlikler açıklanmaktadır.

|Araç kutusu adı|Etkinlik|Açıklama|
|------------------|--------------|-----------------|
|**Durum**|[StateActivity](https://msdn2.microsoft.com/library/system.workflow.activities.stateactivity.aspx)|Durum makinesindeki bir durumu temsil eder; , ek **StateActivity** etkinlikleri içerebilir. Daha fazla bilgi için bkz. [StateActivity etkinliğini kullanma](https://msdn2.microsoft.com/library/bb628612.aspx).|
|**SetState**|[SetStateActivity](https://msdn2.microsoft.com/library/system.workflow.activities.setstateactivity.aspx)|Yeni bir duruma geçiş belirtir. Daha fazla bilgi için bkz. [SetStateActivity etkinliğini kullanma](https://msdn2.microsoft.com/library/bb628469.aspx).|
|**StateInitialization**|[StateInitializationActivity](https://msdn2.microsoft.com/library/system.workflow.activities.stateinitializationactivity.aspx)|Bir durum girildiğinde yürütülür; , diğer etkinlikleri içerebilir. Daha fazla bilgi için bkz. [StateInitialization etkinliğini kullanma](https://msdn2.microsoft.com/library/bb675253.aspx).|
|**Statesonlandırılması**|[StateFinalizationActivity](https://msdn2.microsoft.com/library/system.workflow.activities.statefinalizationactivity.aspx)|[StateActivity](https://msdn2.microsoft.com/library/system.workflow.activities.stateactivity.aspx) etkinliğinden çıkarken içerilen etkinlikleri yürütür. Daha fazla bilgi için bkz. [StateFinalizationActivity etkinliğini kullanma](https://msdn2.microsoft.com/library/bb675278.aspx).|
|**EventDriven**|[EventDrivenActivity](https://msdn2.microsoft.com/library/system.workflow.activities.eventdrivenactivity.aspx)|Yürütmeye başlamak için bir dış olaya güvenen durumlar için kullanılır. **EventDrivenActivity** etkinliğinin ilk alt etkinlik olarak [IEventActivity](https://msdn2.microsoft.com/library/system.workflow.activities.ieventactivity.aspx) arabirimini uygulayan bir etkinliği olmalıdır. Daha fazla bilgi için bkz. [EventDrivenActivity etkinliğini kullanma](https://msdn2.microsoft.com/library/bb628466.aspx).|

 Bir durum makinesi iş akışındaki ana bileşen [StateActivity](https://msdn2.microsoft.com/library/system.workflow.activities.stateactivity.aspx) etkinliğidir. Olaylar bir durum makinesi iş akışındaki çeşitli noktalarda yakalandığından, olaylarla ilişkili görevleri işlemek için farklı durumlar girilir. İş akışı ömrü boyunca iş akışı bırakabilir ve birkaç farklı durum girebilir. Bu durumlar [SetStateActivity](https://msdn2.microsoft.com/library/system.workflow.activities.setstateactivity.aspx) etkinliğini kullanarak birbirlerine bağlanır.

 İş akışı tasarım yüzeyine yeni bir **StateActivity** sürüklediğinizde, alt etkinlikler olarak [EventDrivenActivity](https://msdn2.microsoft.com/library/system.workflow.activities.eventdrivenactivity.aspx), [StateInitializationActivity](https://msdn2.microsoft.com/library/system.workflow.activities.stateinitializationactivity.aspx), [StateFinalizationActivity](https://msdn2.microsoft.com/library/system.workflow.activities.statefinalizationactivity.aspx)veya ek **StateActivity** etkinlikleri ekleyebilirsiniz.

> [!CAUTION]
> İş akışları oluşturmak için durum makinesi iş akışı tasarımcısını kullandığınızda, **Belge anahat** görünümü penceresi ile tasarlamakta olduğunuz iş akışının yapısını izlemeniz gerekir. **Belge anahat** görünümü penceresinde durum makinesi iş akışı yapısının görünümü, iş akışı işaretleme dosyasındaki etkinliklerin mantıksal yerleşimini yansıtır. İş akışı etkinliklerinin tasarım yüzeyinde göründükleri fiziksel düzeni, iş akışı işaretleme dosyasındaki etkinliklerin mantıksal yerleşimini yansıtmayabilir.
>
> **Belge Anahattı** penceresini açmak Için, **Görünüm** menüsünde **diğer pencereler**' in üzerine gelin ve **Belge Anahattı**' nı seçin.

## <a name="see-also"></a>Ayrıca Bkz.
 [Nasıl yapılır: durum makinesi Iş akışı konsol uygulamaları oluşturma (eski)](../workflow-designer/how-to-create-state-machine-workflow-console-applications-legacy.md) [nasıl yapılır: bir durum makinesi iş akışı kitaplığı (eski)](../workflow-designer/how-to-create-a-state-machine-workflow-library-legacy.md) [durum makinesi Iş akışlarını](https://msdn2.microsoft.com/library/bb628601.aspx) [kullanarak](https://msdn2.microsoft.com/library/bb628612.aspx) [statesonizationactivity](https://msdn2.microsoft.com/library/bb675278.aspx) [etkinliğini kullanarak](https://msdn2.microsoft.com/library/bb628469.aspx) [StateInitializationActivity](https://msdn2.microsoft.com/library/bb675253.aspx) [etkinliğini kullanın](https://msdn2.microsoft.com/library/bb628466.aspx)
