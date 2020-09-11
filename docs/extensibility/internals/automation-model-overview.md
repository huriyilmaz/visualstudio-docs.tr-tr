---
title: Otomasyon modeline genel bakış | Microsoft Docs
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
ms.openlocfilehash: 7f953add14c617d54d44cf8d6bf873c28eea8651
ms.sourcegitcommit: 4b29efeb3a5f05888422417c4ee236e07197fb94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/11/2020
ms.locfileid: "90012171"
---
# <a name="automation-model-overview"></a>Otomasyon modeline genel bakış
Otomasyon modeli, Visual Studio eklentisi veya uzantısı yazabileceğiniz bir nesne kümesinden oluşur. Bir eklenti, Visual Studio ortamını işleyebilen ve ortak görevleri otomatikleştiren bir uygulamadır. Visual Studio uzantısı, özel Visual Studio bileşenleri oluşturabilir veya metin Düzenleyicisi gibi standart bileşenlerin işlevlerine ekleyebilir.

## <a name="objects-in-the-automation-model"></a>Otomasyon modelindeki nesneler
 Otomasyon modeli, ortak ortamın ana modellerini denetleyen ilgili nesne gruplarından oluşur. Aşağıdaki diyagramda, otomasyon modelini oluşturan kapsamlı Visual Studio nesneleri kümesi gösterilmektedir.

 ![Visual Studio Otomasyon nesne grafiği](../../extensibility/internals/media/vsvisualstudioautomationobjectchart.gif "vsVisualStudioAutomationObjectChart")

 Daha fazla bilgi için bkz. [Visual Studio Ortamını Genişletme](/previous-versions/esk3eey8(v=vs.140)).

 Ortam, farklı işlevsel alanlara yönelik bir model sağlar. Örneğin, kodda bulabileceğiniz çeşitli öğeler için bir kod modeli vardır. Çeşitli belge öğeleri için bir belge modeli vardır. Tek bir alan olan proje alanı, VSPackage sağlayıcılarına özellikle ilgilenmektedir. Büyük olasılıkla yeni proje türlerinizi Otomasyon modeline aynı şekilde katkıda bulunmak [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] ve [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] Otomasyon modeliyle katkıda bulunmak isteyeceksiniz. Bu işlem, [VSPackages için Otomasyon sağlama](../../extensibility/internals/providing-automation-for-vspackages.md)bölümünde özetlenmiştir.

 Ortamın otomasyon modelini genişletmeyi düşünebileceğiniz yerleri şunlardır:

- Project

- Belge

- Kod

- Oluşturma

Otomasyon hakkında daha fazla bilgi için bkz. [Visual Studio Için Otomasyon ve genişletilebilirlik](../../vs-2015/extensibility/extensibility-in-visual-studio.md?view=vs-2015). Bu belge ve bağlantı sağladığı belgeler, VSPackage için nasıl Otomasyon sağlayacağınızla ilgili kararlar almanıza yardımcı olur.

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl yapılır: eklenti oluşturma](/previous-versions/80493a3w(v=vs.140))