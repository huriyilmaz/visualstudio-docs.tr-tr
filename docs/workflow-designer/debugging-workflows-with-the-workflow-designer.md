---
title: İş Akışı Tasarımcısı ile İş Akışlarında Hata Ayıklama
description: Hata ayıklayıcısının İş Akışı Tasarımcısı hata ayıklayıcısına benzer bir işlemle iş akışlarının ve özel etkinliklerin Visual Studio öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio Workflow Designer [WFD], debugging workflows
- Workflow Designer [WFD], debugging workflows
ms.assetid: d71308cf-d464-4536-8711-0d0a8eadb255
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-workflow-designer
ms.workload:
- multiple
ms.openlocfilehash: 454f916a80cda1b2b485cc6385218bfc88fb0490
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122155245"
---
# <a name="debug-workflows-with-the-workflow-designer"></a>İş Akışı Tasarımcısı ile iş akışlarını İş Akışı Tasarımcısı

Bu **İş Akışı Tasarımcısı** iş akışlarını ve özel etkinliklerde hata ayıklama olanağı sağlar. İşlem ve davranış, varsayılan hata ayıklayıcısının Visual Studio benzerdir.

## <a name="invoke-the-workflow-debugger"></a>İş akışı hata ayıklayıcısını çağırma

Genel olarak, iş akışlarının hata ayıklaması, diğer programlama dillerinde yazılan programlarda Visual Studio ayıklar. İş akışı hata ayıklayıcısını aşağıdaki yollarla başlatabilirsiniz:

- İş **akışı örneğinin** çalışan **konak işlemini seçmek** için Hata Ayıklama menüsünde İşleme Ekle'yi seçin. Bu yordam, yönetilen kodda bir konak işlemi eklemekle aynıdır.

- İş akışının bir örneğini çalıştırmaya başlamak veya bir kesme noktası isabet olduktan sonra çalışmaya devam etmek için **F5** tuşuna basın.

- Uzaktan hata ayıklamayı kullanın. Uzaktan hata ayıklama kullanma hakkında daha fazla bilgi için [bkz. Nasıl 2. Adım: Uzaktan hata ayıklamayı etkinleştirme.](/previous-versions/visualstudio/visual-studio-2010/febz73k0(v=vs.100))

   > [!NOTE]
   > İş akışı uygulaması x86 mimarisini hedeflese ve 64 bit işletim sistemi çalıştıran bir makinede barındırıldısa, uzak makineye Visual Studio yüklenmediği veya iş akışı uygulamasının hedefi Herhangi bir CPU olarak değiştirilene kadar uzaktan hata ayıklama **çalışmaz.**

## <a name="step-through-code"></a>Kodda adım adım ilerler

- **Adım:** F11 tuşuna basarak bir **etkinliğin içine adımla.** Hata ayıklayıcısı, tanımlanan herhangi bir işleyiciye gider. İşleyici tanımlanmamışsa, etkinliğin üzerine adımlar veya diğer etkinlikleri içeren bileşik etkinliklerle ilk yürütülen etkinliğin içine adımlarnız.

- **Dışarı Adımla:** Shift F11 tuşuna basarak **bir** + **etkinliğin dışında adım at.** Bir etkinliğin dışında adımlama, geçerli etkinliği ve tüm onun tüm kardeleme etkinliklerini tamamlamaya çalıştırır. Ardından hata ayıklayıcısı geçerli etkinliğin üst öğesi üzerinde kesmeler. Kod işleyiciden çıkarılırken, hata ayıklayıcı işleyicinin ilişkilendiril olduğu etkinlikte hata ayıklayıcıyı kırar.

- **Adım Adım:** F10 tuşuna basarak bir **etkinliğin üzerine adımla.** Bileşik etkinliğin üzerine adımlarken, hata ayıklayıcı bileşik etkinliğin ilk yürütülebilir alt bilgisinde hata ayıklayıcıyı kırar. Bir etkinlik gibi bileşik olmayan bir adım atılırken, hata ayıklayıcı etkinliği ve ilişkili işleyicilerini yürütür ve <xref:System.Activities.Statements.Assign> sonraki etkinlikte sonlar. Yürütülen etkinlik bileşik etkinlikte son alt etkinlikse, yürütmeden sonra hata ayıklayıcı üst etkinlikte son olur.

## <a name="debug-with-f5"></a>F5 ile hata ayıklama

bir İş akışı konsol uygulaması inşa ediyorsanız, uygulamanıza ve iş akışınıza hata ayıklamaya başlamak için **F5** tuşuna basmanız gerekir. Etkinlik kitaplığını kendi başına inşa ediyorsanız, başlangıç projesi olarak yürütülebilir bir konak uygulaması belirtmeniz gerekir. içinde bir başlangıç projesi **ayarlamak Çözüm Gezgini,** ana bilgisayar projesi adına sağ tıklayın ve Başlangıç Olarak Ayarla'yı seçin **Project.**
