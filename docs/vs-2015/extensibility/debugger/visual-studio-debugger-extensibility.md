---
title: Visual Studio hata ayıklayıcısı genişletilebilirliği | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Visual Studio], Debugging SDK
- Debugging SDK
ms.assetid: c088b6a2-c3ad-446b-830d-9c6f41b2934b
caps.latest.revision: 33
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0b8d37954bf238b2ed1323bf021fded94ec0c584
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "73983661"
---
# <a name="visual-studio-debugger-extensibility"></a>Visual Studio Hata Ayıklayıcı Genişletilebilirliği
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Visual Studio, programınızda hata izlemek için güçlü ve kullanımı kolay bir araç sağlayan tam bir etkileşimli kaynak kodu hata ayıklayıcısı içerir. Hata ayıklayıcı, Visual Basic, C#, C/C++ ve JavaScript için kapsamlı destek içerir. Bununla birlikte, [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] [Microsoft İndirme Merkezi](https://www.microsoft.com/download/details.aspx?id=21835)' nden erişilebilen diğer programlama dilleri, hata ayıklayıcıda aynı zengin özelliklerle desteklenebilir.  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]Hata ayıklayıcı genel ön uç (yani, Kullanıcı arabirimi) hata ayıklama bileşenlerinde, bu da hata ayıklamakta olan dile özgüdür. Yeni diller için, hata ayıklayıcı tarafından destek için gerekli olan her şey, [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] hata ayıklama altyapısı (de) gibi gerekli arka uç bileşenlerini oluşturmaktır. Bu, ' nin [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] geldiği yerdir.  
  
 , [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Yenı bir de oluşturmak için gereken tüm öğelere yönelik kapsamlı bir başvuru içerir. Ayrıca, başlamanıza yardımcı olacak örnekler ve öğreticiler de vardır.  
  
 Hata ayıklama desteğiyle bir dil projesi sisteminin uçtan uca bir örneği için bkz. [IronPython örneği](https://msdn.microsoft.com/4c41695c-12c1-4670-b43b-d8d84c9e4089).  
  
 Aşağıdaki bölümlerde, kullanarak hata ayıklayıcının nasıl genişletileceği açıklanır [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] .  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Başlarken](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]Hata ayıklama tekliflerinin ve SDK 'nın nasıl yükleneceğini açıklar.  
  
 [Özel Hata Ayıklama Altyapısı Oluşturma](../../extensibility/debugger/creating-a-custom-debug-engine.md)  
 Özel DE sürecini, programınızı bir DE ile ayırmak için hazırlamaktan bir de belgeler.  
  
 [CLR İfade Değerlendirici Yazma](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)  
 Bir ifade değerlendirici yazmanız gerekip gerekmediğini açıklar.  
  
 [Hata Ayıklama Altyapısı Uygulama Stratejisi Seçme](../../extensibility/debugger/choosing-a-debug-engine-implementation-strategy.md)  
 ' Nin nasıl uygulanacağını açıklar.  
  
 [Başvuru](../../extensibility/debugger/reference/reference-visual-studio-debugging-apis.md)  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]Hata ayıklama API 'sini belgeler.  
  
 [Örnekler](../../extensibility/debugger/visual-studio-debugging-samples.md)  
 Ortak dil çalışma zamanı ifadesi değerlendirici örneğine ve bir hata ayıklama altyapısı örneğine bağlantılar içerir.
