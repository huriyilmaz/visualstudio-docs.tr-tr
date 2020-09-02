---
title: 'Nasıl yapılır: bul ve Değiştir mekanizmasını uygulama | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - find and replace
ms.assetid: bbd348db-3d19-42eb-99a2-3e808528c0ca
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d4362d0b0c3f013ce6f38d13265dcc181c77012c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62548704"
---
# <a name="how-to-implement-the-find-and-replace-mechanism"></a>Nasıl Yapılır: Bul ve Değiştir Mekanizması Uygulama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio, Bul/Değiştir uygulamamanın iki yolunu sağlar. Bir yol, bir metin görüntüsünü kabuğa geçirmek ve metni aramayı, vurgulamayı ve değiştirmeyi sağlamak için bir yoldur. Bu, kullanıcıların birden çok metin yaymalarını belirlemesine olanak sağlar. Alternatif olarak, VSPackage bu işlevin kendisini denetleyebilir. Her iki durumda da, geçerli hedef ve tüm açık belgelerin hedefleri hakkında, kabuğa bildirimde bulunmalıdır.  
  
### <a name="to-implement-findreplace"></a>Bul/Değiştir uygulamak için  
  
1. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget>Arabirimini çerçeve özellikleri veya tarafından döndürülen nesnelerden birine uygulayın <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID> <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID> . Özel bir düzenleyici oluşturuyorsanız, bu arabirimi özel düzenleyici sınıfının bir parçası olarak uygulamalısınız.  
  
2. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.GetCapabilities%2A>Düzenleyicinizi desteklediği seçenekleri belirtmek ve metin resmi aramasını uygulayıp uygulamadığını göstermek için yöntemini kullanın.  
  
     Düzenleyiciniz metin resmi aramasını destekliyorsa, uygulayın <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.GetSearchImage%2A> .  
  
     Aksi takdirde, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Find%2A> ve uygulayın <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Replace%2A> .  
  
3. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Find%2A>Ve <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Replace%2A> yöntemlerini uygularsanız, arabirimini çağırarak arama görevlerinizi kolaylaştırabilirsiniz <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindHelper> .  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindHelper>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Find%2A>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.GetSearchImage%2A>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Replace%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID>
