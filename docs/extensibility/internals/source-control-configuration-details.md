---
title: Kaynak denetimi yapılandırma ayrıntıları | Microsoft Docs
description: Visual Studio 'da, proje sisteminizin veya düzenleyicinizin izin istemek üzere yapılandırılmasını içeren bir proje türü için kaynak denetimi uygulama hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], configuration details
ms.assetid: adbee9fc-7a2e-4abe-a3b8-e6615bcd797f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a5c93e690922057116b395bed3881627e8a37847
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105069355"
---
# <a name="source-control-configuration-details"></a>Kaynak Denetimi Yapılandırma Ayrıntıları
Kaynak denetimi uygulamak için, aşağıdakileri yapmak üzere proje sisteminizi veya düzenleyiciyi doğru şekilde yapılandırmanız gerekir:

- Değiştirilen duruma geçiş için izin iste

- Dosya kaydetme izni iste

- Projede dosya ekleme, kaldırma veya yeniden adlandırma izni iste

## <a name="request-permission-to-transition-to-changed-state"></a>Değiştirilen duruma geçiş için Izin iste
 Bir proje veya düzenleyici, çağırarak değiştirilen (kirli) duruma geçiş için izin istemelidir <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> . Uygulayan her düzenleyici, <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData.IsDocDataDirty%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> için döndürmeden önce belgeyi ortamda değiştirmek için onayı çağırmalıdır ve onay almalıdır `True` <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData.IsDocDataDirty%2A> . Bir proje aslında proje dosyası için bir düzenleyicidir ve sonuç olarak proje dosyası için değiştirilen durum izlemenin, dosyaları için bir metin düzenleyicisi olarak uygulanması için aynı sorumluluğa sahiptir. Ortam, çözümün değiştirilmiş durumunu işler, ancak çözümün başvurduğu, ancak depolamadığı herhangi bir nesnenin değiştirilen durumunu işlemeniz gerekir, çünkü proje dosyası ya da onun öğeleri gibi. Genel olarak, projeniz veya düzenleyiciniz bir öğe için kalıcılığı yönetmekten sorumludur, bu durumda değiştirilen durum izlemeyi uygulamaktan sorumludur.

 Çağrıya yanıt olarak `IVsQueryEditQuerySave2::QueryEditFiles` , ortam şunları yapabilir:

- Değişiklik çağrısını reddedin, bu durumda düzenleyicinin veya projenin değiştirilmemiş (temiz) durumda kalması gerekir.

- Belge verilerinin yeniden yüklenmesi gerektiğini gösterir. Bir proje için ortam, projenin verilerini yeniden yükler. Bir düzenleyici, verileri diskten uygulamasının uygulamasına yeniden yüklemesi gerekir <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.ReloadDocData%2A> . Her iki durumda da, veriler yeniden yüklendiğinde proje veya düzenleyicideki bağlam değişebilir.

  `IVsQueryEditQuerySave2::QueryEditFiles`Var olan bir kod tabanı üzerine uygun çağrıları geriye doğru sığdırmak için karmaşık ve zor bir görevdir. Sonuç olarak, bu çağrılar proje ya da düzenleyicinin oluşturulması sırasında tümleştirilebilmelidir.

## <a name="request-permission-to-save-a-file"></a>Dosya kaydetme Izni iste
 Bir proje veya düzenleyici bir dosyayı kaydetmeden önce, <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFile%2A> veya çağırmalıdır <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A> . Proje dosyaları için, bu çağrılar çözüm tarafından otomatik olarak tamamlanır ve bir proje dosyasının ne zaman kaydedileceğini bilir. Düzenleyici, bir yardımcı işlevi kullanmadığı için düzenleyiciler bu çağrıları yapmaktan sorumludur `IVsPersistDocData2` <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SaveDocDataToFile%2A> . Düzenleyiciniz `IVsPersistDocData2` Bu şekilde uyguluyorsa, `IVsQueryEditQuerySave2::QuerySaveFile` veya çağrısı `IVsQueryEditQuerySave2::QuerySaveFiles` sizin için yapılır.

> [!NOTE]
> Bu çağrıları her zaman preemptively yapın — diğer bir deyişle, düzenleyiciniz bir iptal alabilir.

## <a name="request-permission-to-add-remove-or-rename-files-in-the-project"></a>Projede dosya ekleme, kaldırma veya yeniden adlandırma Izni iste
 Bir proje bir dosya veya dizin ekleyebilmeniz, yeniden adlandırabilmeniz veya kaldırabilmesi `IVsTrackProjectDocuments2::OnQuery*` için, ortamdan izin istemek üzere uygun yöntemi çağırmalıdır. İzin verildiğinde, projenin işlemi tamamlaması ve sonra `IVsTrackProjectDocuments2::OnAfter*` işlemin tamamlandığını ortama bildirmek için uygun yöntemi çağırması gerekir. Projenin, <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> yalnızca üst dosyaları değil, tüm dosyalar (örneğin, özel dosyalar) için arabirim yöntemlerini çağırması gerekir. Dosya çağrıları zorunludur, ancak dizin çağrıları isteğe bağlıdır. Projenizde dizin bilgileri varsa, ilgili <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> yöntemleri çağırmalıdır, ancak bu bilgileri içermiyorsa ortam dizin bilgilerini çıkarmaz.

 Proje, `IVsTrackProjectDocuments2` Proje Aç veya Kapat ' ın yöntemlerini çağırmamalıdır. Başlangıçta bu bilgileri isteyen dinleyiciler olay için bekleyebilir <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenSolution%2A> ve ihtiyaç duydukları bilgileri bulmak için çözüm aracılığıyla yineleyebilirsiniz. Kapatılırken, bu bilgiler gerekli değildir. `IVsTrackProjectDocuments2` , öğesinden sağlanır <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments> .

 Her ekleme, yeniden adlandırma ve kaldırma eylemi için bir `OnQuery*` Yöntem ve bir `OnAfter*` Yöntem vardır. `OnQuery*`Dosya veya dizin ekleme, yeniden adlandırma veya kaldırma izni istemek için yöntemini çağırın. `OnAfter*`Dosya veya dizin eklendikten, yeniden adlandırıldıktan veya kaldırıldıktan sonra ve proje durumu yeni durumu yansıtdıktan sonra yöntemi çağırın.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFile%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SaveDocDataToFile%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>
- [Kaynak Denetimini Destekleme](../../extensibility/internals/supporting-source-control.md)
