---
title: Visual Studio Hata ayıklayıcı genişletilebilirliği | Microsoft Docs
description: bu makalede Visual Studio hata ayıklayıcı genişletilebilirliği açıklanmakta ve Visual Studio hata ayıklama hakkında makalelerin bağlantıları verilmektedir.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Visual Studio], Debugging SDK
- Debugging SDK
ms.assetid: c088b6a2-c3ad-446b-830d-9c6f41b2934b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 153b5006db591ca12cf4e27e6715ccb8cd0fcb37
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126626331"
---
# <a name="visual-studio-debugger-extensibility"></a>Visual Studio hata ayıklayıcı genişletilebilirliği
Visual Studio, programınızda hata izlemek için güçlü ve kullanımı kolay bir araç sağlayan tam bir etkileşimli kaynak kodu hata ayıklayıcısı içerir. hata ayıklayıcı Visual Basic, C#, C/C++ ve JavaScript için kapsamlı desteğe sahiptir. Bununla birlikte, [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] [Microsoft İndirme Merkezi](https://www.microsoft.com/download/details.aspx?id=21835)' nden erişilebilen diğer programlama dilleri, hata ayıklayıcıda aynı zengin özelliklerle desteklenebilir.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Hata ayıklayıcı genel ön uç (yani, Kullanıcı arabirimi) hata ayıklama bileşenlerinde, bu da hata ayıklamakta olan dile özgüdür. Yeni diller için, hata ayıklayıcı tarafından destek için gerekli olan her şey, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] hata ayıklama altyapısı (de) gibi gerekli arka uç bileşenlerini oluşturmaktır. Bu nokta, öğesinin [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] geldiği yerdir.

 , [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Yenı bir de oluşturmak için gereken tüm öğelere yönelik kapsamlı bir başvuru içerir. Ayrıca, başlamanıza yardımcı olacak örnekler ve öğreticiler de vardır.

 Hata ayıklama desteğiyle bir dil projesi sisteminin tamamen bir örneği için bkz. [IronPython örneği](https://www.microsoft.com/download/details.aspx?id=55984).

 Aşağıdaki bölümlerde, kullanarak hata ayıklayıcının nasıl genişletileceği açıklanır [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] .

## <a name="in-this-section"></a>Bu bölümde
 [Kullanmaya](../../extensibility/debugger/getting-started-with-debugger-extensibility.md) başlayın [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Hata ayıklama tekliflerinin ve SDK 'nın nasıl yükleneceğini açıklar.

 [Özel hata ayıklama altyapısı oluşturma](../../extensibility/debugger/creating-a-custom-debug-engine.md) Özel DE sürecini, programınızı bir DE ile ayırmak için hazırlamaktan bir de belgeler.

 [Clr ifade değerlendiricisi yazma](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md) Bir ifade değerlendirici yazmanız gerekip gerekmediğini açıklar.

 [Hata ayıklama altyapısı uygulama stratejisi seçin](../../extensibility/debugger/choosing-a-debug-engine-implementation-strategy.md) ' Nin nasıl uygulanacağını açıklar.

 [Başvuru](../../extensibility/debugger/reference/reference-visual-studio-debugging-apis.md) [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Hata ayıklama API 'sini belgeler.

 [Örnekler](../../extensibility/debugger/visual-studio-debugging-samples.md) Ortak dil çalışma zamanı ifadesi değerlendirici örneğine ve bir hata ayıklama altyapısı örneğine bağlantılar içerir.
