---
title: Birlikte çalışma derlemelerindeki komut sözleşmeleri | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- command handling with interop assemblies, command contracts
- interop assemblies, command contracts
ms.assetid: 57245708-f539-42dc-8963-2754a48f0189
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 50d48d3a8ff55559cce1c3a40142e31b8eebd85f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68195131"
---
# <a name="command-contracts-in-interop-assemblies"></a>Birlikte Çalışma Bütünleştirilmiş Kodlarında Komut Sözleşmeleri
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Arabirim aracılığıyla komutları işlemeye yönelik temel sözleşme, <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> ortamın, <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> özelliğin desteklenip desteklenmediğini ve desteklenip desteklenmediğini, durumunu ve metnini belirlemede, desteklenip desteklenmediğini belirlemede metodunu çağırdığı durumdur. Daha sonra ortam, <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> komutu yürütmek için yöntemini çağırır.  
  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>Yöntemi tüm komutlar için aynı şekilde işlenir. Gerekirse daha fazla iletişim (örneğin, açılan listelerle), <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> yöntemi uygun parametrelerle çağırarak yönetilir. Bu parametrelerin yorumu, belirtilen komuta bağlıdır.  
  
 Komut hedefi çıkış parametresindeki değerleri döndürürse, çağıran tüm kaynakları boşaltmaktan her zaman sorumludur. Bu parametre bir değişken olduğundan, varyantın temizlenmesi kaynakları serbest bırakır.  
  
 Komutların bir hiyerarşi penceresi içinde çalışması gereken durumlarda, <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> arabirimin kullanılması gerekir. <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>Arabirim, benzer yöntemlere sahip benzer bir sözleşmeye sahiptir: <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> ve <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A> .  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [VSPackages Kullanıcı arabirimi öğeleri ekleme](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [VSPackages 'de komut yönlendirme](../../extensibility/internals/command-routing-in-vspackages.md)   
 [Uygulama](../../extensibility/internals/command-implementation.md)
