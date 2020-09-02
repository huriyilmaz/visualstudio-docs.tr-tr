---
title: 'Nasıl yapılır: başka bir düzenleyicide düzenleyici barındırma | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - host a nested editor
ms.assetid: 2b0eb705-fe94-4ca8-93e0-9dbd8ce61a44
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4d4b4ff425feb22b5057a8d1a76b7f73b8932d9f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204174"
---
# <a name="how-to-host-an-editor-in-another-editor"></a>Nasıl Yapılır: Bir Düzenleyiciyi Başka Bir Düzenleyicide Barındırma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio 'da, ana pencere olarak barındırma penceresini belirterek bir düzenleyiciyi diğeri içinde barındırabilirsiniz. Bunu yapmak için, parametreleri <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2> ve <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2> alt pencere çerçevesini ayarlayın.  
  
### <a name="to-set-up-the-window-frame-to-host-an-editor"></a>Bir düzenleyiciyi barındırmak için pencere çerçevesini ayarlamak için  
  
1. Bir alt pencere bölmesi oluşturarak bir düzenleyiciyi barındırılan düzenleyici olarak belirleyin.  
  
     Bu bölme, düzenleyicinin metninin gidececektir.  
  
2. Or metodunu kullanarak barındırma düzenleyiciyi oluşturun <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenSpecificEditor%2A> .  
  
3. <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2> <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2> Bu özellikleri sırasıyla yöntemine parametre olarak geçirerek barındırılan düzenleyicinin pencere çerçeve uygulamasındaki ve özelliklerini ayarlayın <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.SetProperty%2A> .  
  
     Bu parametreleri almanız gerekiyorsa, bu özellikleri <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> metoduna geçirin.  
  
4. <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A>Kapsanan düzenleyici için yöntemini çağırın.  
  
     Düzenleyici, kapsayan düzenleyicinin barındırılan bölmesinde görünür.  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Mimarlar için Visual Studio Team Edition 'daki **Uygulama Tasarımcısı** , başka bir düzenleyiciyi barındıran bir düzenleyici pencere çerçevesinin bir örneğidir. **Uygulama Tasarımcısı** sağ bölmedeki diğer tasarımcıları barındırır. İçerilen tasarımcıların her biri için bir tasarımcı paneli (veya **Özellikler** sayfası), kapsayan pencere çerçevesine eklenir.
