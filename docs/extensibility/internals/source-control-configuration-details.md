---
title: Kaynak denetimi yapılandırma ayrıntıları | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], configuration details
ms.assetid: adbee9fc-7a2e-4abe-a3b8-e6615bcd797f
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0a6c51dfe4ad9378af04da61dbd7e9011c4678f1
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72723791"
---
# <a name="source-control-configuration-details"></a>Kaynak Denetimi Yapılandırma Ayrıntıları
Kaynak denetimi uygulamak için, aşağıdakileri yapmak üzere proje sisteminizi veya düzenleyiciyi doğru şekilde yapılandırmanız gerekir:

- Değiştirilen duruma geçiş için izin iste

- Dosya kaydetme izni iste

- Projede dosya ekleme, kaldırma veya yeniden adlandırma izni iste

## <a name="request-permission-to-transition-to-changed-state"></a>Değiştirilen duruma geçiş için Izin iste
 Proje veya düzenleyicinin <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>çağırarak değiştirilen (kirli) duruma geçiş izni istemesi gerekir. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData.IsDocDataDirty%2A> uygulayan her düzenleyici, <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData.IsDocDataDirty%2A>için `True` döndürmeden önce <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> çağırmalıdır ve belgeyi ortamdan değiştirmek için onay almalıdır. Bir proje aslında proje dosyası için bir düzenleyicidir ve sonuç olarak proje dosyası için değiştirilen durum izlemenin, dosyaları için bir metin düzenleyicisi olarak uygulanması için aynı sorumluluğa sahiptir. Ortam, çözümün değiştirilmiş durumunu işler, ancak çözümün başvurduğu, ancak depolamadığı herhangi bir nesnenin değiştirilen durumunu işlemeniz gerekir, çünkü proje dosyası ya da onun öğeleri gibi. Genel olarak, projeniz veya düzenleyiciniz bir öğe için kalıcılığı yönetmekten sorumludur, bu durumda değiştirilen durum izlemeyi uygulamaktan sorumludur.

 `IVsQueryEditQuerySave2::QueryEditFiles` çağrısına yanıt olarak, ortam şunları yapabilir:

- Değişiklik çağrısını reddedin, bu durumda düzenleyicinin veya projenin değiştirilmemiş (temiz) durumda kalması gerekir.

- Belge verilerinin yeniden yüklenmesi gerektiğini gösterir. Bir proje için ortam, projenin verilerini yeniden yükler. Bir düzenleyici, verileri diskten <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.ReloadDocData%2A> uygulamasına yeniden yüklemeli. Her iki durumda da, veriler yeniden yüklendiğinde proje veya düzenleyicideki bağlam değişebilir.

  Mevcut bir kod tabanına uygun `IVsQueryEditQuerySave2::QueryEditFiles` çağrılarını geriye doğru uydurmak için karmaşık ve zor bir görevdir. Sonuç olarak, bu çağrılar proje ya da düzenleyicinin oluşturulması sırasında tümleştirilebilmelidir.

## <a name="request-permission-to-save-a-file"></a>Dosya kaydetme Izni iste
 Proje veya düzenleyici bir dosyayı kaydetmeden önce, <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFile%2A> veya <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A>çağırmalıdır. Proje dosyaları için, bu çağrılar çözüm tarafından otomatik olarak tamamlanır ve bir proje dosyasının ne zaman kaydedileceğini bilir. `IVsPersistDocData2` Düzenleyicisi, <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SaveDocDataToFile%2A>yardımcı işlevini kullanmadığı takdirde, düzenleyiciler bu çağrıları yapmaktan sorumludur. Düzenleyiciniz bu şekilde `IVsPersistDocData2` uygularsa, `IVsQueryEditQuerySave2::QuerySaveFile` veya `IVsQueryEditQuerySave2::QuerySaveFiles` çağrısı sizin için yapılır.

> [!NOTE]
> Bu çağrıları her zaman preemptively yapın — diğer bir deyişle, düzenleyiciniz bir iptal alabilir.

## <a name="request-permission-to-add-remove-or-rename-files-in-the-project"></a>Projede dosya ekleme, kaldırma veya yeniden adlandırma Izni iste
 Bir proje bir dosya veya dizin ekleyebilmeniz, yeniden adlandırabilmeniz veya kaldırabilmesi için, ortamdan izin istemek üzere uygun `IVsTrackProjectDocuments2::OnQuery*` yöntemini çağırmalıdır. İzin verildiğinde, projenin işlemi tamamlaması ve sonra işlemin tamamlandığını ortama bildirmek için uygun `IVsTrackProjectDocuments2::OnAfter*` yöntemini çağırması gerekir. Proje, yalnızca üst dosyaları değil, tüm dosyalar (örneğin, özel dosyalar) için <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> arabiriminin yöntemlerini çağırmalıdır. Dosya çağrıları zorunludur, ancak dizin çağrıları isteğe bağlıdır. Projenizde dizin bilgileri varsa, uygun <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> yöntemleri çağırmalıdır, ancak bu bilgileri içermiyorsa, ortam dizin bilgilerini çıkarmaz.

 Proje açık veya kapalı proje `IVsTrackProjectDocuments2` yöntemlerini çağırmamalıdır. Başlangıçta bu bilgilerin başlamasını isteyen dinleyiciler <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenSolution%2A> olayı bekleyebilir ve gereksinim duydukları bilgileri bulmak için çözüm üzerinden yineleyebilirsiniz. Kapatılırken, bu bilgiler gerekli değildir. `IVsTrackProjectDocuments2` <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>sağlanır.

 Her ekleme, yeniden adlandırma ve kaldırma eylemi için bir `OnQuery*` yöntemi ve bir `OnAfter*` yöntemi vardır. Dosya veya dizin ekleme, yeniden adlandırma veya kaldırma izni istemek için `OnQuery*` yöntemini çağırın. Dosya veya dizin eklendikten, yeniden adlandırıldıktan veya kaldırıldıktan sonra ve proje durumu yeni durumu yansıttığından `OnAfter*` yöntemi çağırın.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFile%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SaveDocDataToFile%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>
- [Kaynak Denetimini Destekleme](../../extensibility/internals/supporting-source-control.md)