---
title: 'Nasıl yapılır: Içerik Haritası gezintisini kullanma | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: 4a688056-37dc-406a-9071-be2141e192fe
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 1c01e48e6aa34513e57b373150c605cb0a7f5b18
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72659147"
---
# <a name="how-to-use-breadcrumb-navigation"></a>Nasıl Yapılır: İçerik Haritası Gezintisini Kullanma
İçinde görüntülenen etkinlik kümesini değiştirmek için üç ana yol vardır [!INCLUDE[wfd1](../includes/wfd1-md.md)] :

1. Alt etkinliğin ayrıntısına gitmek için çift tıklayın.

2. Bir üst etkinliğe gitmek için içerik haritası çubuğundaki bir düğmeye tıklayın.

3. Etkinlikleri yerinde genişletin veya daraltın.

### <a name="using-breadcrumb-navigation"></a>İçerik haritası gezintisini kullanma

1. [!INCLUDE[wfd2](../includes/wfd2-md.md)]Kök etkinliği tıklatılan etkinlik olarak değiştirmek için bir etkinliğe çift tıklayın. Tıklanan etkinlik daha sonra kökte tamamen genişletilir ve üst öğeleri içerik haritası çubuğunda gösterilir. Bu bazen bir etkinliğin detayına veya dışına gidilme olarak adlandırılır.

2. Geçerli kök etkinliğinin bir üst öğesine gitmek için, içerik haritası çubuğundaki etkinliğe tıklayın.

### <a name="expanding-or-collapsing-an-activity-in-place"></a>Etkinlik yerinde genişletiliyor veya daralliyor

1. Bir etkinliğin köşeli ayraçlarını tıklatmak, etkinliği yerinde genişletir veya daraltır.

2. Genişletme durumunun durumu düğme tıklatılarak değiştirildiğinde, genişletmenin yeni durumu XAML 'ye kaydedilir.

    > [!WARNING]
    > Tüm etkinlikler yerinde genişletilebilecek. Bir etkinliğin bir yerde genişletilmediği iki durum vardır: etkinliğin üst öğesi alt öğelerinin yerinde genişletilmesini sağlamıyor, (örneğin, bir akış çizelgesi içindeki etkinlikler yerinde genişletilemez) veya etkinlik Tasarımcısı kendine ait bir yerde genişleme izin vermez. ' De dahil olan etkinlik [!INCLUDE[wfd2](../includes/wfd2-md.md)] tasarımcılarının hiçbiri ikinci davranışa sahip olsa da bazı özel etkinlikler bu davranışı gösterebilir.

### <a name="expanding-all-or-collapsing-all-activities"></a>Tüm etkinlikleri genişletme veya daraltma

1. Geçerli içerik haritası kökündeki tüm etkinlikleri genişletmek veya daraltmak için Kullanıcı arabirimindeki tümünü **Genişlet** ve **Tümünü Daralt** düğmelerini kullanın. Tümünü Genişlet ve Tümünü Daralt genel durumlardır. Yani, içerik haritası gezintisi kullanarak kök etkinliği değiştirdiğinizde, **geri yükle**' ye tıklaana kadar Tümünü Genişlet veya Tümünü Daralt durumu devam ettirir.

2. Tümünü Genişlet veya Tümünü Daralt durumunu uyguladıktan sonra, her etkinliğe daha önce uygulanan duruma bakmak için geri dönerek görüntülenen **geri yükle** düğmesine tıklayabilirsiniz.

    > [!WARNING]
    > Örneğin, gibi bir etkinlik <xref:System.Activities.Statements.Flowchart> Genişlemeden sonra, **Tümünü Genişlet** ve **Tümünü Daralt** düğmeleri Ile ilişkili işlevler, **akış çizelgesi** tasarımcısında devre dışıdır. [!INCLUDE[crabout](../includes/crabout-md.md)]**akış çizelgesi** Tasarımcısı, bkz. [akış çizelgesi](../workflow-designer/flowchart-activity-designer.md) konusu.

    > [!WARNING]
    > Tümünü Genişlet, **Switch** ve **TryCatch** etkinlik tasarımcıları 'nda özel bir etkiye de sahiptir. **Tümünü Genişlet**' e tıkladığınızda tüm anahtar örnekleri ve tüm dene/yakala/finally blokları görüntülenir. Tümünü **geri yükle** veya **Daralt** ' a tıkladığınızda bu tasarımcılar varsayılan durumlarına döndürülür. Bu, içeriğini görüntülemek için tek bir servis talebine/bloğa tıklayabilirsiniz.