---
title: Çözüm Kullanıcı Seçenekleri (. Suo) Dosya | Microsoft Docs
description: İkili biçimde depolanan yapılandırılmış bir depolama dosyasında kullanıcı başına çözüm seçeneklerini içeren çözüm kullanıcı seçenekleri (.suo) dosyası hakkında bilgi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- .suo files, VSPackages
- suo files, VSPackages
- solutions, .suo files
- solutions, user options
- solution user options (.suo) file
ms.assetid: 75258e0d-600d-4a3d-94f4-3d7ac12cb47c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: cacbd9d9b8348e4404b035906d047229fb52839b9bed2178149cb90a0e0d93a2
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121337766"
---
# <a name="solution-user-options-suo-file"></a>Çözüm Kullanıcı Seçenekleri (.Suo) Dosyası
Çözüm kullanıcı seçenekleri (.suo) dosyası, kullanıcı başına çözüm seçeneklerini içerir. Bu dosya, kaynak kodu denetimine iade edilmelidir.

 Çözüm kullanıcı seçenekleri (.suo) dosyası, ikili biçimde depolanan yapılandırılmış bir depolama veya bileşik dosyadır. Kullanıcı bilgilerini akışlara kaydetmek için akışın adı .suo dosyasındaki bilgileri tanımlamak için kullanılacak anahtardır. Çözüm kullanıcı seçenekleri dosyası, kullanıcı tercihi ayarlarını depolamak için kullanılır ve bir çözüm kayded Visual Studio otomatik olarak oluşturulur.

 Ortam bir .suo dosyası açtığında, o anda yüklü olan tüm VSPackage'ları numaralar. Bir VSPackage arabirimini uygulayıyorsa, ortam VSPackage üzerinde yöntemini çağırarak .suo dosyasından tüm verilerini <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts> <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.LoadUserOptions%2A> yüklemesini istiyor.

 .suo dosyasına hangi akışları yazılmış olabileceğini bilmek VSPackage'ın sorumluluğundadır. Yazdığı her akış için VSPackage, anahtarıyla tanımlanan ve akışın adı olan belirli bir akışı yüklemek için aracılığıyla ortama <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.LoadPackageUserOpts%2A> geri çağrır. Ortam daha sonra vsPackage'a geri çağırarak akışın adını ve yönteminin işaretçisini geçen belirli `IStream` bir akışı <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.LoadPackageUserOpts%2A> okur.

 Bu noktada , .suo dosyasının okunan başka bir bölümü olup ola bir çağrı `LoadUserOptions` yapılır. Bu işlem, .suo dosyasındaki tüm veri akışları ortam tarafından okunana ve işlenene kadar devam eder.

 Çözüm kaydedilebilir veya kapatılmıştır, ortam yöntemi <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.SavePackageSolutionProps%2A> işaretçisi ile yöntemini <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.SaveUserOptions%2A> çağırmaktadır. Kaydediyecek ikili bilgileri içeren bir yöntemine geçirilebilir, ardından bilgileri .suo dosyasına yazar ve .suo dosyasına yazacak başka bir bilgi akışı olup ola bir bilgi akışı olup ola bir daha görmek için yöntemini yeniden `IStream` <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.WriteUserOptions%2A> `SaveUserOptions` çağırır.

 Bu iki yöntem olan ve , işaretçisini .suo dosyasına kaydeden her bilgi akışı için `SaveUserOptions` `WriteUserOptions` recursively olarak `IVsSolutionPersistence` çağrılır. Birden çok akışın .suo dosyasına yaz çağrılmalarına izin vermek için bunlar tekrarlı olarak çağrılır. Bu şekilde, kullanıcı bilgileri çözümde kalıcı olur ve çözüm bir sonraki açıldığında orada olması garanti olur.

## <a name="see-also"></a>Ayrıca bkz.
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts>
- [Çözümler](../../extensibility/internals/solutions-overview.md)
