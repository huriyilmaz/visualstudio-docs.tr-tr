---
title: 'İş Akışı Tasarımcısı-nasıl yapılır: Içerik Haritası gezintisini kullanma'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 4a688056-37dc-406a-9071-be2141e192fe
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d7a851ea074a78349c9e52ef127bf2814d203bf5
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72650310"
---
# <a name="how-to-use-breadcrumb-navigation"></a>Nasıl yapılır: Içerik Haritası gezintisini kullanma

İş Akışı Tasarımcısı ' de görüntülenen etkinlik kümesini değiştirmek için üç ana yol vardır:

1. Alt etkinliğin ayrıntısına gitmek için çift tıklayın.

2. Bir üst etkinliğe gitmek için içerik haritası çubuğundaki bir düğmeye tıklayın.

3. Etkinlikleri yerinde genişletin veya daraltın.

## <a name="using-breadcrumb-navigation"></a>İçerik haritası gezintisini kullanma

1. Kök etkinliği tıklatılan etkinlik olarak değiştirmek için İş Akışı Tasarımcısı etkinliğine çift tıklayın. Tıklanan etkinlik daha sonra kökte tamamen genişletilir ve üst öğeleri içerik haritası çubuğunda gösterilir. Bu bazen bir etkinliğin detayına veya dışına gidilme olarak adlandırılır.

2. Geçerli kök etkinliğinin bir üst öğesine gitmek için, içerik haritası çubuğundaki etkinliğe tıklayın.

## <a name="expanding-or-collapsing-an-activity-in-place"></a>Etkinlik yerinde genişletiliyor veya daralliyor

1. Bir etkinliğin köşeli ayraçlarını tıklatmak, etkinliği yerinde genişletir veya daraltır.

2. Genişletme durumunun durumu düğme tıklatılarak değiştirildiğinde, genişletmenin yeni durumu XAML 'ye kaydedilir.

    > [!WARNING]
    > Tüm etkinlikler yerinde genişletilebilecek. Bir etkinliğin bir yerde genişletilmediği iki durum vardır: etkinliğin üst öğesi alt öğelerinin yerinde genişletilme yapmasına izin vermez (örneğin, bir akış çizelgesi içindeki etkinlikler yerinde genişletilemez) veya etkinlik Tasarımcısı kendine kendisine izin vermez yerinde genişletilir. İş Akışı Tasarımcısı ' de yer alan etkinlik tasarımcılarının hiçbiri ikinci davranışa sahip olsa da, bazı özel etkinlikler bu davranışı gösterebilir.

## <a name="expanding-all-or-collapsing-all-activities"></a>Tüm etkinlikleri genişletme veya daraltma

1. Geçerli içerik haritası kökündeki tüm etkinlikleri genişletmek veya daraltmak için Kullanıcı arabirimindeki tümünü **Genişlet** ve **Tümünü Daralt** düğmelerini kullanın. Tümünü Genişlet ve Tümünü Daralt genel durumlardır. Yani, içerik haritası gezintisi kullanarak kök etkinliği değiştirdiğinizde, **geri yükle**' ye tıklaana kadar Tümünü Genişlet veya Tümünü Daralt durumu devam ettirir.

2. Tümünü Genişlet veya Tümünü Daralt durumunu uyguladıktan sonra, her etkinliğe daha önce uygulanan duruma bakmak için geri dönerek görüntülenen **geri yükle** düğmesine tıklayabilirsiniz.

    > [!WARNING]
    > @No__t_0 gibi bir etkinlik Genişlemeden sonra, **Tümünü Genişlet** ve **Tümünü Daralt** düğmeleri Ile Ilişkili işlevler, **akış çizelgesi** tasarımcısında devre dışıdır. **Akış çizelgesi** Tasarımcısı hakkında daha fazla bilgi için, bkz. [akış çizelgesi](../workflow-designer/flowchart-activity-designer.md) konusu.

    > [!WARNING]
    > Tümünü Genişlet, **Switch** ve **TryCatch** etkinlik tasarımcıları 'nda özel bir etkiye de sahiptir. **Tümünü Genişlet**' e tıkladığınızda tüm anahtar örnekleri ve tüm dene/yakala/finally blokları görüntülenir. Tümünü **geri yükle** veya **Daralt** ' a tıkladığınızda bu tasarımcılar varsayılan durumlarına döndürülür. Bu, içeriğini görüntülemek için tek bir servis talebine/bloğa tıklayabilirsiniz.