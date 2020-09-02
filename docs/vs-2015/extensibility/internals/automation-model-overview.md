---
title: Otomasyon modeline genel bakış | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], about automation
- extensibility
ms.assetid: 12b6d6db-0d22-4aaa-aa7d-1365f759b7b0
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e17164976062ec916074c6210be6ae42e8ea1d03
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65699496"
---
# <a name="automation-model-overview"></a>Otomasyon Modeline Genel Bakış
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Otomasyon modeli, Visual Studio eklentisi veya uzantısı yazabileceğiniz bir nesne kümesinden oluşur. Bir eklenti, Visual Studio ortamını işleyebilen ve ortak görevleri otomatikleştiren bir uygulamadır. Visual Studio uzantısı, özel Visual Studio bileşenleri oluşturabilir veya metin Düzenleyicisi gibi standart bileşenlerin işlevlerine ekleyebilir.  
  
## <a name="objects-in-the-automation-model"></a>Otomasyon modelindeki nesneler  
 Otomasyon modeli, ortak ortamın ana modellerini denetleyen ilgili nesne gruplarından oluşur. Aşağıda, otomasyon modelini oluşturan nesnelerin kapsamlı bir kümesini gösteren bir diyagram verilmiştir.  
  
 ![Visual Studio Otomasyon nesne grafiği](../../extensibility/internals/media/vsvisualstudioautomationobjectchart.gif "vsVisualStudioAutomationObjectChart")  
Visual Studio Automation nesneleri  
  
 Daha fazla bilgi için bkz. [Visual Studio Ortamını Genişletme](https://msdn.microsoft.com/library/4173a963-7ac7-4966-9bb7-e28a9d9f6792).  
  
 Ortam, farklı işlevsel alanlara yönelik bir model sağlar. Örneğin, kodda bulabileceğiniz çeşitli öğeler için bir kod modeli vardır. Çeşitli belge öğeleri için bir belge modeli vardır. Tek bir alan olan proje alanı, VSPackage sağlayıcılarına özellikle ilgilenmektedir. Büyük olasılıkla yeni proje türlerinizi Otomasyon modeline aynı şekilde katkıda bulunmak [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] ve [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] Otomasyon modeliyle katkıda bulunmak isteyeceksiniz. Bu işlem, [VSPackages Için Otomasyon sağlamaya](../../extensibility/internals/providing-automation-for-vspackages.md)yöneliktir.  
  
 Ortamın otomasyon modelini genişletmeyi düşünebileceğiniz yerleri şunlardır:  
  
- Project  
  
- Belge  
  
- Kod  
  
- Oluşturma  
  
  Otomasyon hakkında daha fazla bilgi için bkz. [Visual Studio Için Otomasyon ve genişletilebilirlik](https://msdn.microsoft.com/library/f71a2253-3e68-4e5e-9a18-edbba816caf6). Bu belge ve bağlantı sağladığı belgeler, VSPackage için nasıl Otomasyon sağlayacağınızla ilgili kararlar almanıza yardımcı olur.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: eklenti oluşturma](https://msdn.microsoft.com/library/50be56d2-e3a5-4cd2-8569-2a0666b268ce)
