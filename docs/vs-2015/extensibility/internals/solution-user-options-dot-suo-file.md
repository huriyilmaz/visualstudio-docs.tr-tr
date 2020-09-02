---
title: Çözüm Kullanıcı seçenekleri (. Suo) dosyası | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- .suo files, VSPackages
- suo files, VSPackages
- solutions, .suo files
- solutions, user options
- solution user options (.suo) file
ms.assetid: 75258e0d-600d-4a3d-94f4-3d7ac12cb47c
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1a9825fabe08940e8950cf88a1dbf2bc149af0b2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68197333"
---
# <a name="solution-user-options-suo-file"></a>Çözüm Kullanıcı Seçenekleri (.Suo) Dosyası
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Çözüm Kullanıcı seçenekleri (. suo) dosyası, Kullanıcı başına çözüm seçeneklerini içerir. Bu dosya kaynak kodu denetimine iade edilmelidir.  
  
 Çözüm Kullanıcı seçenekleri (. suo) dosyası, bir ikili biçimde depolanan yapılandırılmış bir depolama veya bileşik bir dosyadır. Kullanıcı bilgilerini,. suo dosyasındaki bilgileri tanımlamak için kullanılacak anahtar olan akışın adı ile akışlara kaydedersiniz. Çözüm Kullanıcı seçenekleri dosyası, Kullanıcı tercihi ayarlarını depolamak için kullanılır ve Visual Studio bir çözüm kaydettiğinde otomatik olarak oluşturulur.  
  
 Ortam bir. suo dosyası açtığında, o anda yüklü olan tüm VSPackages 'leri numaralandırır. Bir VSPackage arabirimini uyguluyorsa <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts> , ortam, <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.LoadUserOptions%2A> tüm verilerini. suo dosyasından yüklemesini ısteyen VSPackage üzerinde yöntemini çağırır.  
  
 Bu,. suo dosyasına hangi akışların yazıldığını bilmeyen VSPackage 'ın sorumluluğundadır. Yazdığı her akış için, VSPackage, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.LoadPackageUserOpts%2A> akışın adı olan anahtar tarafından tanımlanan belirli bir akışı yüklemek için ortamına geri çağırır. Daha sonra ortam, akışın adını ve yöntemine bir işaretçi geçiren söz konusu akışın okunması için VSPackage 'a geri çağrı yapılır `IStream` <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.LoadPackageUserOpts%2A> .  
  
 Bu noktada, `LoadUserOptions` . suo dosyasının okunması gereken başka bir bölümü olup olmadığını görmek için başka bir çağrı yapılır. Bu işlem,. suo dosyasındaki tüm veri akışları ortam tarafından okunana ve işlenene kadar devam eder.  
  
 Çözüm kaydedildiğinde veya kapatıldığında, ortam yöntemini <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.SavePackageSolutionProps%2A> yöntemine yönelik bir işaretçi ile çağırır <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.SaveUserOptions%2A> . `IStream`Kaydedilecek ikili bilgileri içeren bir <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.WriteUserOptions%2A> yöntemi yöntemine geçirilir, daha sonra bilgileri. suo dosyasına yazar ve `SaveUserOptions` . suo dosyasına yazılacak başka bir bilgi akışı olup olmadığını görmek için yöntemi yeniden çağırır.  
  
 Bu iki yöntem `SaveUserOptions` ve `WriteUserOptions` ,. suo dosyasına kaydedilecek her bilgi akışı için yinelemeli olarak çağrılır `IVsSolutionPersistence` . Birden çok akışının. suo dosyasına yazılmasına izin vermek için yinelemeli olarak adlandırılırlar. Bu şekilde, Kullanıcı bilgileri çözümle kalıcı hale getirilir ve çözüm bir dahaki sefer açıldığında garanti edilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts>   
 [Çözümler](../../extensibility/internals/solutions-overview.md)
