---
title: Otomasyon Modeline Genel Bakış | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], about automation
- extensibility
ms.assetid: 12b6d6db-0d22-4aaa-aa7d-1365f759b7b0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7b940677c370106ebdcc63c7984d553003251e8a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710004"
---
# <a name="automation-model-overview"></a>Otomasyon modeline genel bakış
Otomasyon modeli, Visual Studio eklentisi veya uzantısı yazabileceğiniz bir nesne kümesinden oluşur. Eklenti, Visual Studio ortamını işleyen ve ortak görevleri otomatikleştirebilen bir uygulamadır. Visual Studio uzantısı özel Visual Studio bileşenleri oluşturabilir veya metin düzenleyicisi gibi standart bileşenlerin işlevselliğini ekleyebilir.

## <a name="objects-in-the-automation-model"></a>Otomasyon modelindeki nesneler
 Otomasyon modeli, ortak ortamın ana yönlerini kontrol eden ilgili nesne gruplarından oluşur. Aşağıdaki diyagram, otomasyon modelini oluşturan geniş Visual Studio nesne kümesini gösterir.

 ![Visual Studio otomasyon nesne grafiği](../../extensibility/internals/media/vsvisualstudioautomationobjectchart.gif "vsVisualStudioAutomationObjectChart")

 Daha fazla bilgi için Visual [Studio ortamını genişlet'e](https://msdn.microsoft.com/Library/4173a963-7ac7-4966-9bb7-e28a9d9f6792)bakın.

 Ortam farklı işlevsel alanlar için bir model sağlar. Örneğin, kodda bulabileceğiniz çeşitli öğeler için bir kod modeli vardır. Çeşitli belge öğeleri için bir belge modeli vardır. Bir alan, proje alanı, VSPackage sağlayıcıları için özel bir ilgi alanıdır. Büyük olasılıkla yeni proje tiplerinizin otomasyon modeline olduğu gibi [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] katkıda bulunmasını ve otomasyon modeline katkıda bulunmasını isteyeceksiniz. Bu işlem [VSPackages için otomasyon sağlayın'da](../../extensibility/internals/providing-automation-for-vspackages.md)özetlenmiştir.

 Ortamın otomasyon modelini genişletmeyi düşünebileceğiniz yerler:

- Project

- Belge

- Kod

- Yapı

Otomasyon hakkında daha fazla bilgi için [Visual Studio için Otomasyon ve genişletilebilirlik bilgisine](/visualstudio/extensibility/extensibility-in-visual-studio?view=vs-2015)bakın. Bu belge ve bağlantı sağladığı belgeler, VSPackage'ınız için otomasyonu nasıl sağlamanız gerektiğine ilişkin kararlar vermenize yardımcı olur.

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl yapılsın: Eklenti oluşturma](https://msdn.microsoft.com/Library/50be56d2-e3a5-4cd2-8569-2a0666b268ce)
