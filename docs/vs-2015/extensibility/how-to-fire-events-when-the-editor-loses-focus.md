---
title: 'Nasıl yapılır: düzenleyici odağı kaybettiğinde olayları ateşle | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - fire events on losing focus
ms.assetid: 64d40695-6917-468a-8037-a253453ac159
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2ebca733798636ca32787b88b8874c31a2ffffdb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204200"
---
# <a name="how-to-fire-events-when-the-editor-loses-focus"></a>Nasıl Yapılır: Düzenleyici Odağı Kaybettiğinde Olayları Başlatma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bazen bir düzenleyicinin pencere çerçevesinde odağı kaybettiğini bilmeleri gerekir. Örneğin, düzenleyiciye artık odaklanmadan kodu bir kod penceresinden ayıklamanız gerekebilir. Aşağıdaki yordam, odağı kaybetmekte olan düzenleyicinin bildirimini almak için İzlenecek adımları sağlar.  
  
### <a name="to-fire-an-event-in-response-to-an-editor-losing-focus"></a>Odağı kaybeden bir düzenleyiciye yanıt olarak bir olay tetiklemesi  
  
1. İçinden bir nesne alarak seçim olaylarını izleyin <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection> <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> .  
  
2. <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.AdviseSelectionEvents%2A>Bunu çağırın ve nesneniz olarak belirtin <xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents> .  
  
3. Çağrımızda öğesine <xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents.OnElementValueChanged%2A> bakın `elementid==SEID_WindowFrame` .  
  
4. `varValueNew`Parametreyi iki şey için test edin:  
  
    1. Aradığınız pencere çerçevesi.  
  
    2. Programınızın seçimi bu pencere çerçevesinde kaybettiğini belirten nokta.
