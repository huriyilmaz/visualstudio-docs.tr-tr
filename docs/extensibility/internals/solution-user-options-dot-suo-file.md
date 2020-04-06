---
title: Çözüm Kullanıcı Seçenekleri (. Suo) Dosya | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- .suo files, VSPackages
- suo files, VSPackages
- solutions, .suo files
- solutions, user options
- solution user options (.suo) file
ms.assetid: 75258e0d-600d-4a3d-94f4-3d7ac12cb47c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9469663d3ac258e1c568778894d8584c68c13632
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705311"
---
# <a name="solution-user-options-suo-file"></a>Çözüm Kullanıcı Seçenekleri (.Suo) Dosyası
Çözüm kullanıcı seçenekleri (.suo) dosyası kullanıcı başına çözüm seçenekleri içerir. Bu dosya kaynak kodu denetimi için iade edilmemelidir.

 Çözüm kullanıcı seçenekleri (.suo) dosyası, ikili biçimde depolanan yapılandırılmış bir depolama veya bileşikdosyadır. Kullanıcı bilgilerini,.suo dosyasındaki bilgileri tanımlamak için kullanılacak anahtar olan akış adıyla akışlara kaydedersiniz. Çözüm kullanıcı seçenekleri dosyası, kullanıcı tercihi ayarlarını depolamak için kullanılır ve Visual Studio bir çözüm kaydettiğinde otomatik olarak oluşturulur.

 Ortam bir .suo dosyasını açtığında, şu anda yüklenen tüm VSPackages'ı kaydeder. Bir VSPackage <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts> arabirimi uygularsa, ortam <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.LoadUserOptions%2A> VSPackage'daki yöntemi çağırır ve tüm verilerini .suo dosyasından yüklemesini ister.

 .suo dosyasına hangi akışları yazmış olabileceğini bilmek VSPackage'ın sorumluluğundadır. Yazdığı her akış için VSPackage, akışın adı <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.LoadPackageUserOpts%2A> olan anahtarla tanımlanan belirli bir akışı yüklemek için ortama geri çağırır. Ortam daha sonra, akışın adını ve `IStream` <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.LoadPackageUserOpts%2A> metodun işaretçisini geçen belirli akışı okumak için VSPackage'a geri çağırır.

 Bu noktada, .suo `LoadUserOptions` dosyasının okunması gereken başka bir bölümü olup olmadığını görmek için başka bir arama yapılır. Bu işlem,.suo dosyasındaki tüm veri akışları ortam tarafından okunup işlenene kadar devam eder.

 Çözüm kaydedildiğinde veya kapatıldığında, ortam <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.SavePackageSolutionProps%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.SaveUserOptions%2A> yöntemi yönteme işaretçiyle çağırır. Kaydedilecek ikili bilgileri içeren bir `IStream` <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.WriteUserOptions%2A> yöntem, daha sonra .suo dosyasına bilgi yazar `SaveUserOptions` ve .suo dosyasına yazAcak başka bir bilgi akışı olup olmadığını görmek için yöntemi tekrar çağırır.

 Bu iki `SaveUserOptions` yöntem `WriteUserOptions`ve , işaretçide `IVsSolutionPersistence`geçen .suo dosyasına kaydedilecek her bilgi akışı için özyinelemeli olarak adlandırılır. .suo dosyasına birden çok akış yazılmasına izin vermek için özyinelemeli olarak adlandırılırlar. Bu şekilde, kullanıcı bilgileri çözümle devam etti ve çözüm bir sonraki açıldığında orada olacağı garanti edilir.

## <a name="see-also"></a>Ayrıca bkz.
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts>
- [Çözümler](../../extensibility/internals/solutions-overview.md)
