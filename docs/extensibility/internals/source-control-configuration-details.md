---
title: Kaynak Kontrol Yapılandırma Detayları | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], configuration details
ms.assetid: adbee9fc-7a2e-4abe-a3b8-e6615bcd797f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7cf4a5c55e8093e5dcd6406cde1c60f642188495
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705290"
---
# <a name="source-control-configuration-details"></a>Kaynak Denetimi Yapılandırma Ayrıntıları
Kaynak denetimini uygulamak için, proje sisteminizi veya düzenleyicinizi aşağıdakileri yapacak şekilde düzgün bir şekilde yapılandırmanız gerekir:

- Değiştirilen duruma geçiş için izin isteme

- Dosyayı kaydetmek için izin isteme

- Projeye dosya eklemek, kaldırmak veya yeniden adlandırmak için izin isteme

## <a name="request-permission-to-transition-to-changed-state"></a>Değiştirilen Duruma Geçiş İzni İsteyin
 Bir proje veya düzenleyici, değiştirilen (kirli) duruma geçiş <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>için ' yi arayarak izin istemelidir. Uygulayan her düzenleyici, <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> belgeyi çevreden değiştirmek `True` için <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData.IsDocDataDirty%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData.IsDocDataDirty%2A> aramalı ve onay almalıdır. Proje aslında bir proje dosyasının düzenleyicisidir ve sonuç olarak, bir metin düzenleyicisinin dosyaları için yaptığı gibi proje dosyası için değiştirilen durum izlemeyi uygulamayla aynı sorumluluğa sahiptir. Ortam çözümün değiştirilen durumunu işler, ancak çözüm başvuruları yapılan ancak proje dosyası veya öğeleri gibi depolanmayan herhangi bir nesnenin değiştirilen durumunu işlemeniz gerekir. Genel olarak, projeniz veya düzenleyiciniz bir öğenin kalıcılığını yönetmekle sorumluysa, değiştirilen durum izlemeyi uygulamaktan sorumludur.

 Çağrıya `IVsQueryEditQuerySave2::QueryEditFiles` yanıt olarak, ortam aşağıdakileri yapabilir:

- Değişiklik çağrısını reddedin, bu durumda düzenleyici veya proje değişmeden (temiz) durumda kalmalıdır.

- Belge verilerinin yeniden yüklenmesi gerektiğini belirtin. Bir proje için ortam, proje için verileri yeniden yükler. Bir düzenleyici, <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.ReloadDocData%2A> uygulama yoluyla diskten verileri yeniden yüklemelidir. Her iki durumda da, veriler yeniden yüklendiğinde projedeki veya düzenleyicideki bağlam değişebilir.

  Uygun `IVsQueryEditQuerySave2::QueryEditFiles` çağrıları varolan bir kod tabanına yenilemek karmaşık ve zor bir görevdir. Sonuç olarak, bu çağrılar proje veya düzenleyici oluşturma sırasında tümleşik olmalıdır.

## <a name="request-permission-to-save-a-file"></a>Dosyayı Kaydetmek İçin İzin İsteyin
 Bir proje veya düzenleyici bir dosyayı <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFile%2A> kaydetmeden önce, araması veya <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A>. Proje dosyaları için bu çağrılar, proje dosyasını ne zaman kaydedinen çözüm tarafından otomatik olarak tamamlanır. Editörler yardımcı işlevini `IVsPersistDocData2` <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SaveDocDataToFile%2A>kullanır editör uygulaması sürece bu aramaları yapmak için sorumludur. Düzenleyiciniz bu `IVsPersistDocData2` şekilde uygularsa, arama `IVsQueryEditQuerySave2::QuerySaveFile` `IVsQueryEditQuerySave2::QuerySaveFiles` sizin için yapılır.

> [!NOTE]
> Bu aramaları her zaman önceden yapın, yani düzenleyicinizin iptal edilebildiği bir zamanda.

## <a name="request-permission-to-add-remove-or-rename-files-in-the-project"></a>Projeye Dosya Eklemek, Kaldırmak veya Yeniden AdlandırmaK İçin İzin İsteyin
 Bir proje bir dosya veya dizin eklemeden, yeniden adlandırabilmek `IVsTrackProjectDocuments2::OnQuery*` veya kaldırabilmek için, ortamdan izin istemek için uygun yöntemi araması gerekir. İzin verilirse, proje işlemi tamamlamalı ve ardından ortamın tamamladığını bildirmek için uygun `IVsTrackProjectDocuments2::OnAfter*` yöntemi aramalıdır. Proje, tüm dosyalar (örneğin, özel dosyalar) için <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> arabirimin yöntemlerini çağırmalı ve sadece ana dosyaları değil. Dosya aramaları zorunludur, ancak dizin aramaları isteğe bağlıdır. Projenizde dizin bilgisi varsa, uygun <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> yöntemleri çağırmalıdır, ancak bu bilgilere sahip değilse, ortam dizin bilgilerini çıkaracaktır.

 Proje, proje açık veya `IVsTrackProjectDocuments2` kapalı yöntem aramamalıdır. Başlangıçta bu bilgileri isteyen dinleyiciler <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenSolution%2A> etkinliği bekleyebilir ve gereksinim duydukları bilgileri bulmak için çözüm üzerinden yinelenebilir. Kapatma da bu bilgilere gerek yoktur. `IVsTrackProjectDocuments2`'den <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>sağlanmaktadır.

 Her ekleme, yeniden adlandırma ve eylemi kaldırma `OnQuery*` için `OnAfter*` bir yöntem ve yöntem vardır. Dosya `OnQuery*` veya dizini eklemek, yeniden adlandırmak veya kaldırmak için izin istemek için yöntemi arayın. Dosya `OnAfter*` veya dizin eklendikten, yeniden adlandırıldıktan veya kaldırıldıktan ve proje durumu yeni durumu yansıttığından sonra yöntemi arayın.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFile%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SaveDocDataToFile%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>
- [Kaynak Denetimini Destekleme](../../extensibility/internals/supporting-source-control.md)
