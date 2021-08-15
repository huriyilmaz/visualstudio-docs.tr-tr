---
title: Otomasyon Modeline Genel Bakış | Microsoft Docs
description: Bir eklenti Visual Studio uzantısını yazarak bir dizi nesneden oluşan Visual Studio otomasyon modeli hakkında bilgi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], about automation
- extensibility
ms.assetid: 12b6d6db-0d22-4aaa-aa7d-1365f759b7b0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 24fdf3e87e4e8e58237052527e595bd60908373388d1e127f2607c88a609bfac
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121432779"
---
# <a name="automation-model-overview"></a>Otomasyon modeline genel bakış
Otomasyon modeli, eklenti veya uzantı için bir Visual Studio nesne kümesi içerir. Eklenti, uygulama ortamını yönetip ortak görevleri Visual Studio bir uygulamadır. Bir Visual Studio, özel Visual Studio bileşenleri oluşturabilir veya metin düzenleyicisi gibi standart bileşenlerin işlevselliğine ekleyebilir.

## <a name="objects-in-the-automation-model"></a>Otomasyon modelinde nesneler
 Otomasyon modeli, ortak ortamın ana modellerini kontrol altına alan ilgili nesne gruplarından oluşur. Aşağıdaki diyagramda otomasyon modelini Visual Studio nesnelerinin kapsamlı bir kümesi yer alıyor.

 ![Visual Studio otomasyon nesne grafiği](../../extensibility/internals/media/vsvisualstudioautomationobjectchart.gif "vsVisualStudioAutomationObjectChart")

 Daha fazla bilgi için [bkz. Visual Studio genişletme.](/previous-versions/esk3eey8(v=vs.140))

 Ortam, farklı işlevsel alanlar için bir model sağlar. Örneğin, kodda bul olabileceğiniz çeşitli öğeler için bir kod modeli vardır. Çeşitli belge öğeleri için bir belge modeli vardır. Proje alanı olan bir alan, VSPackage sağlayıcıları için özellikle ilgi alanıdır. Yeni proje türlerinizi büyük olasılıkla otomasyon modeliyle aynı şekilde katkıda bulunarak otomasyon modeline [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] katkıda bulunun. Bu işlem [VSPackage'lar için otomasyon sağlama içinde açıklandı.](../../extensibility/internals/providing-automation-for-vspackages.md)

 Ortamın otomasyon modelini genişletmeyi düşünebilecekleri yerler:

- Project

- Belge

- Kod

- Oluşturma

Otomasyon hakkında daha fazla bilgi için bkz. Visual Studio için [otomasyon ve genişletilebilirlik.](/previous-versions/visualstudio/visual-studio-2015/extensibility/extensibility-in-visual-studio?preserve-view=true&view=vs-2015) Bu belge ve bağlantı sağladığı belgeler, VSPackage'nız için nasıl otomasyon sağlamanız gerektiğiyle ilgili kararlar a yardımcı olur.

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl: Eklenti oluşturma](/previous-versions/80493a3w(v=vs.140))