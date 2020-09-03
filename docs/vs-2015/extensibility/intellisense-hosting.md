---
title: IntelliSense barındırma | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - IntelliSense hosting
ms.assetid: 20c61f8a-d32d-47e2-9c67-bf721e2cbead
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a5c378aec6822a436de0d8fc2656fcac7be4149f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68203901"
---
# <a name="intellisense-hosting"></a>IntelliSense Barındırma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio IntelliSense barındırılmasına izin vermez. Intellsense barındırma, Visual Studio metin Düzenleyicisi tarafından barındırılmayan kod için IntelliSense sağlamanıza olanak tanır.  
  
## <a name="intellisense-hosting-usage"></a>IntelliSense barındırma kullanımı  
 Visual Studio 'da, bir tamamlanma kümesine ve bir metin arabelleğine erişimi olan tüm kodlar, IntelliSense pencerelerini Kullanıcı arabirimi (UI) içinde herhangi bir yerden alabilir. Bunun bazı örnek senaryoları, **Gözcü** penceresinde veya bir kesme noktası özellikleri penceresinin Koşul alanında tamamlanmalarıdır.  
  
### <a name="implementation-interfaces"></a>Uygulama arabirimleri  
  
#### <a name="ivsintellisensehost"></a>IVsIntellisenseHost  
 IntelliSense açılır penceresi barındıran herhangi bir kullanıcı arabirimi bileşeni <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> arabirimi desteklemelidir. Varsayılan çekirdek Düzenleyicisi metin görünümü, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> geçerli IntelliSense işlevini koruyacak bir stok arabirimi uygulamasını içerir. Çoğu bölümde, arabirimin yöntemleri, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> arabirimde uygulanan bir alt kümesini temsil eder <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> . Alt küme, IntelliSense Kullanıcı arabirimi işleme, giriş işareti ve seçim düzenlemesi ve basit metin değiştirme işlevlerini içerir. Ayrıca, arabirim, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> içerik için kullanılan metin arabelleğinde doğrudan mevcut olmayan konular Için IntelliSense 'in sağlanması için ayrı IntelliSense "Subject" ve "Context" i de olanak tanıyor.  
  
#### <a name="ivsintellisensehostgethostflags"></a>IVsIntellisenseHost. GetHostFlags  
 Bir <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> arabirim sağlayıcının, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetHostFlags%2A> bir istemcinin konağın desteklediği IntelliSense özelliklerinin türünü belirlemesini sağlamak için yöntemini uygulaması gerekir.  
  
 [IntelliSenseHostFlags](../extensibility/intellisensehostflags.md)içinde tanımlanan konak bayrakları aşağıda özetlenmiştir.  
  
|IntelliSense ana bilgisayar bayrağı|Açıklama|  
|----------------------------|-----------------|  
|IHF_READONLYCONTEXT|Bu bayrak ayarlandığında, bağlam arabelleğinin salt okunurdur ve düzenlemenin yalnızca konu metninde yer aldığı anlamına gelir.|  
|IHF_NOSEPERATESUBJECT|Bu bayrak ayarlandığında, ayrı bir IntelliSense konusu olmadığı anlamına gelir. Konu, geleneksel IntelliSense sistemindeki gibi bağlam arabelleğinde bulunur <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> .|  
|IHF_SINGLELINESUBJECT|Bu bayrağın ayarlanması, konunun, **Gözcü** penceresinde tek satırlı düzenleme gibi çok satırlı özellikli olmadığı anlamına gelir.|  
|IHF_FORCECOMMITTOCONTEXT|Bu bayrak ayarlandıysa ve bağlam arabelleğinin güncellenmesi gerekiyorsa, ana bilgisayar bağlam arabelleğindeki salt okuma bayrağını yok sayılır ve devam etmek için düzenlemeler sağlar.|  
|IHF_OVERTYPE|Düzenlemenin (konu veya bağlamda) üzerine yazma modunda yapılması gerekir.|  
  
#### <a name="ivsintellisensehostbeforecompletorcommit-and-ivsintellisensehostaftercompletorcommit"></a>IVsIntellisenseHost. Beforetamamlantorcommıt ve IVsIntellisenseHost. Aftertamamlann COMMIT  
 Bu geri arama yöntemleri, ön işleme ve işleme sonrası işlemlerini etkinleştirmek için, metin kaydedilmeden önce ve sonra tamamlanma penceresi tarafından çağrılır.  
  
#### <a name="ivsintellisensecompletor"></a>IVsIntellisenseCompletor  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseCompletor>Arabirim, standart tamamlama penceresinin tümleşik geliştirme ortamı (IDE) tarafından kullanılan ortak hale tablo sürümüdür. Her türlü <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> arabirim, bu tamamlayıcı arabirimini kullanarak IntelliSense 'i hızlıca uygulayabilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualStudio.TextManager.Interop>
