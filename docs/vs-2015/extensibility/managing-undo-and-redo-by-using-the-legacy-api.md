---
title: Eski API 'YI kullanarak geri almayı ve yinelemeyi yönetme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - undo management
ms.assetid: 838c0ddf-fdf3-4df1-8d21-79610b8ba0b1
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7c2133c75b32e56c1a054740bd829bd04cac97cc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68194366"
---
# <a name="managing-undo-and-redo-by-using-the-legacy-api"></a>Eski API'yi Kullanarak Geri Alma ve Yineleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Düzenleyicilerin, kodu değiştirirken kullanıcıların son değişikliklerini geri almasına izin veren geri alma işlemlerini desteklemesi gerekir. Ve altında uygulanan çoğu düzenleyici, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] Tümleşik geliştirme ORTAMı (IDE) tarafından otomatik olarak sağlanmış geri alma desteğine sahip olabilir.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Nasıl Yapılır: Geri Alma Yönetimini Uygulama](../extensibility/how-to-implement-undo-management.md)  
 Tek veya birden çok görünüm içeren düzenleyiciler için geri alma özelliği sağlar.  
  
 [Nasıl Yapılır: Geri Alma Yığınını Temizleme](../extensibility/how-to-clear-the-undo-stack.md)  
 Bir geri alma yığınının nasıl temizleneceğini açıklar.  
  
 [Nasıl Yapılır: Bağlantılı Geri Alma Yönetimini Kullanma](../extensibility/how-to-use-linked-undo-management.md)  
 Bağlantılı geri alma yönetimini düzenleyicinize ekler.  
  
## <a name="reference"></a>Başvuru  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager>  
 Birden çok görünümü destekleyen bir düzenleyici için geri alma yönetimi sağlar.  
  
## <a name="related-sections"></a>İlgili Bölümler
