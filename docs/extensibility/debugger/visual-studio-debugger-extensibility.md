---
title: Visual Studio hata ayıklayıcısı genişletilebilirliği | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Visual Studio], Debugging SDK
- Debugging SDK
ms.assetid: c088b6a2-c3ad-446b-830d-9c6f41b2934b
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9f8a1c2148f25a1e97cfd1369770e056d1cb907d
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72568974"
---
# <a name="visual-studio-debugger-extensibility"></a>Visual Studio hata ayıklayıcı genişletilebilirliği
Visual Studio, programınızda hata izlemek için güçlü ve kullanımı kolay bir araç sağlayan tam bir etkileşimli kaynak kodu hata ayıklayıcısı içerir. Hata ayıklayıcı Visual Basic, C#, C/C++ve JavaScript için kapsamlı desteğe sahiptir. Ancak, [Microsoft Indirme merkezi](http://go.microsoft.com/fwlink/?LinkId=214453)' nden erişilebilen [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)], diğer programlama dilleri hata ayıklayıcıda aynı zengin özelliklerle desteklenebilir.

 @No__t_0 hata ayıklayıcı, hata ayıklama bileşenlerine özel bir ön uç (yani, Kullanıcı arabirimi), bu da hata ayıklanmakta olan dile özgüdür. Yeni diller için, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] hata ayıklayıcı tarafından destek için gerekli olan her şey, hata ayıklama altyapısı (DE) gibi gerekli arka uç bileşenlerini oluşturmaktır. Bu nokta, [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] geldiği yerdir.

 @No__t_0, yeni bir DE oluşturmak için gereken tüm [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] öğelerine yönelik kapsamlı bir başvuru içerir. Ayrıca, başlamanıza yardımcı olacak örnekler ve öğreticiler de vardır.

 Hata ayıklama desteğiyle bir dil projesi sisteminin tamamen bir örneği için bkz. [IronPython örneği](https://www.microsoft.com/download/details.aspx?id=55984).

 Aşağıdaki bölümlerde, [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] kullanarak hata ayıklayıcının nasıl genişletileceği açıklanır.

## <a name="in-this-section"></a>Bu bölümde
 [Kullanmaya](../../extensibility/debugger/getting-started-with-debugger-extensibility.md) başlayın Hangi [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] hata ayıklama tekliflerinin ve SDK 'nın nasıl yükleneceğini açıklar.

 [Özel hata ayıklama altyapısı oluşturma](../../extensibility/debugger/creating-a-custom-debug-engine.md) Özel DE sürecini, programınızı bir DE ile ayırmak için hazırlamaktan bir de belgeler.

 [Clr ifade değerlendiricisi yazma](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md) Bir ifade değerlendirici yazmanız gerekip gerekmediğini açıklar.

 [Hata ayıklama altyapısı uygulama stratejisi seçin](../../extensibility/debugger/choosing-a-debug-engine-implementation-strategy.md) ' Nin nasıl uygulanacağını açıklar.

 [Başvuru](../../extensibility/debugger/reference/reference-visual-studio-debugging-apis.md) @No__t_1 hata ayıklama API 'sini belgeler.

 [Örnekler](../../extensibility/debugger/visual-studio-debugging-samples.md) Ortak dil çalışma zamanı ifadesi değerlendirici örneğine ve bir hata ayıklama altyapısı örneğine bağlantılar içerir.
