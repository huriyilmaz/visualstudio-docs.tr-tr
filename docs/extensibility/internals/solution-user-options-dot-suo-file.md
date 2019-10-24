---
title: Çözüm Kullanıcı seçenekleri (. Suo) dosyası | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- .suo files, VSPackages
- suo files, VSPackages
- solutions, .suo files
- solutions, user options
- solution user options (.suo) file
ms.assetid: 75258e0d-600d-4a3d-94f4-3d7ac12cb47c
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6f21e4a4a6530692709247e64b0d84aa7b06eb3a
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72723808"
---
# <a name="solution-user-options-suo-file"></a>Çözüm Kullanıcı Seçenekleri (.Suo) Dosyası
Çözüm Kullanıcı seçenekleri (. suo) dosyası, Kullanıcı başına çözüm seçeneklerini içerir. Bu dosya kaynak kodu denetimine iade edilmelidir.

 Çözüm Kullanıcı seçenekleri (. suo) dosyası, bir ikili biçimde depolanan yapılandırılmış bir depolama veya bileşik bir dosyadır. Kullanıcı bilgilerini,. suo dosyasındaki bilgileri tanımlamak için kullanılacak anahtar olan akışın adı ile akışlara kaydedersiniz. Çözüm Kullanıcı seçenekleri dosyası, Kullanıcı tercihi ayarlarını depolamak için kullanılır ve Visual Studio bir çözüm kaydettiğinde otomatik olarak oluşturulur.

 Ortam bir. suo dosyası açtığında, o anda yüklü olan tüm VSPackages 'leri numaralandırır. Bir VSPackage <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts> arabirimini uyguluyorsa, ortam, tüm verilerini. suo dosyasından yüklemesini isteyen VSPackage üzerinde <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.LoadUserOptions%2A> yöntemini çağırır.

 Bu,. suo dosyasına hangi akışların yazıldığını bilmeyen VSPackage 'ın sorumluluğundadır. Yazdığı her akış için, VSPackage, akışın adı olan anahtar tarafından tanımlanan belirli bir akışı yüklemek için <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.LoadPackageUserOpts%2A> aracılığıyla ortama geri çağrı yapılır. Daha sonra ortam, akışın adını ve <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.LoadPackageUserOpts%2A> yöntemine `IStream` işaretçiyi geçiren belirli bir akışı okumak için VSPackage 'a geri çağrı yapılır.

 Bu noktada,. suo dosyasının okunması gereken başka bir bölümü olup olmadığını görmek için `LoadUserOptions` başka bir çağrı yapılır. Bu işlem,. suo dosyasındaki tüm veri akışları ortam tarafından okunana ve işlenene kadar devam eder.

 Çözüm kaydedildiğinde veya kapatıldığında, ortam, <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.SaveUserOptions%2A> yöntemine yönelik bir işaretçi ile <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.SavePackageSolutionProps%2A> yöntemini çağırır. Kaydedilecek ikili bilgileri içeren bir `IStream` <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.WriteUserOptions%2A> yöntemine geçirilir ve bu, bilgileri. suo dosyasına yazar ve. suo dosyasına yazılacak başka bir bilgi akışı olup olmadığını görmek için `SaveUserOptions` yöntemini yeniden çağırır.

 Bu iki yöntem `SaveUserOptions` ve `WriteUserOptions`, `IVsSolutionPersistence` işaretçiye geçerek. suo dosyasına kaydedilecek her bilgi akışı için yinelemeli olarak çağırılır. Birden çok akışının. suo dosyasına yazılmasına izin vermek için yinelemeli olarak adlandırılırlar. Bu şekilde, Kullanıcı bilgileri çözümle kalıcı hale getirilir ve çözüm bir dahaki sefer açıldığında garanti edilir.

## <a name="see-also"></a>Ayrıca bkz.
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts>
- [Çözümler](../../extensibility/internals/solutions-overview.md)