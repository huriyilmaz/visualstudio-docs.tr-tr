---
title: Hata İşleme ve Dönüş Değerleri | Microsoft Docs
description: Visual Studio SDK'sı tarafından hata bildirimi alırken zengin hata bilgilerini kaydetmek için birlikte çalışma derlemelerini nasıl sağladığını öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- errors [Visual Studio SDK], handling
- error handling
- return values
ms.assetid: b2d9079d-39a6-438a-8010-290056694b5c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 9f69f998dbfe984a272f86227640fe5eaec51cae
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122152477"
---
# <a name="error-handling-and-return-values"></a>Hata işleme ve dönüş değerleri
VSPackage'lar ve COM hataları için aynı mimariyi kullanır. ve `SetErrorInfo` `GetErrorInfo` işlevleri, Win32 uygulama programlama arabiriminin (API) bir parçasıdır. Tümleşik geliştirme ortamındaki (IDE) herhangi bir VSPackage, hata bildirimi alırken zengin hata bilgilerini kaydetmek için bu genel Win32 API'lerini çağırabilirsiniz. , [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] hata bilgilerini yönetmek için birlikte çalışma derlemeleri sağlar.

## <a name="interop-methods"></a>Birlikte çalışma yöntemleri
 Kolaylık olması için IDE, <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> Win32 API'lerini çağırma yerine kullanmak üzere bir yöntemi sağlar. Yönetilen kodda <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> kullanın. Hata, hata iletisinin görüntülendiğinde (genellikle bir komut işleyicisi uygulayan `HRESULT` nesnedir) IDE uygun ileti kutusunu görüntülemek için başka bir <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> yöntem kullanır. Yönetilen kodda yöntemini <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> kullanın.

 VSPackage uygulayıcısı olarak COM nesneleriniz normalde `ISupportErrorInfo` kullanır. Arabirimi, `ISupportErrorInfo` zengin hata bilgilerini çağrı zincirinin dikey yukarı doğru hareket ettirenin sağlar. İşlemler arasında veya iş parçacıkları arasında kullanılmaktadır nesneler, zengin hata bilgisinin çağırana doğru şekilde sıra olduğundan `ISupportErrorInfo` emin olmak için desteklemesi gerekir.

 VSPackage'larla ilgili ve düzenleyici fabrikaları, düzenleyiciler, hiyerarşiler ve sunulan hizmetler de dahil olmak üzere IDE'nin genişletilen tüm nesneleri zengin hata bilgilerini desteklemesi gerekir. IDE'nin bu VSPackage nesnelerinin uygulaması gerektirilmasa `ISupportErrorInfo` da, her zaman teşvik edilecektir.

 IDE, hata bilgilerini raporlamadan ve IDE'ye her yayıldıklarının [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] `HRESULT` kullanıcıya görüntülenmesinden sorumludur. Nesnelerin oluşturulması için de IDE mekanizması `ErrorInfo` kullanılır.

## <a name="general-guidelines"></a>Genel yönergeler
 VSPackage uygulamanıza yönelik dahili hataları ayarlamak ve rapor etmek <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> için ve yöntemlerini de <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> kullanabilirsiniz. Ancak, genel bir kural olarak VSPackage'lığınıza hata iletilerini işlemeye için şu yönergeleri izleyin:

- `ISupportErrorInfo`VSPackage COM nesnelerinize uygulama.

- uygulayan nesnelerde yöntemini <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> çağıran bir hata raporlama mekanizması <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> oluşturun.

- IDE'nin yöntemi aracılığıyla kullanıcılara hataları görüntülemesine izin <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> verme.

## <a name="error-information-in-the-ide"></a>IDE'de hata bilgileri
 Aşağıdaki kurallar, IDE'de hata bilgilerini [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] işlemeyi gösterir:

- Eski hata bilgisinin kullanıcılara bildirilene bir savunma stratejisi olarak, yöntemini çağıran <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> işlevlerin önce yöntemini çağıran olması <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> gerekir. Önbelleğe `null` alınmış hata iletilerini yeni hata bilgileri ayarlay bir şey çağırmadan önce temizlemek için iletin.

- Hata iletilerini doğrudan rapor yapmayan işlevlerin yalnızca bir hata <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> döndüren yöntemini çağırmalarına izin `HRESULT` verilir. bir işleve girişte veya `ErrorInfo` döndürerek üzerinde temizlemek izin verilen bir değerdir. <xref:Microsoft.VisualStudio.VSConstants.S_OK> Bu kuralın tek istisnası, bir çağrının, alıcı taraf tarafından açıkça kurtarılma veya güvenle yoksayılma `HRESULT` hatası döndüren durumdur.

- Açıkça bir hatayı yoksayan herhangi bir `HRESULT` taraf ile <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> yöntemini çağırması <xref:Microsoft.VisualStudio.VSConstants.S_OK> gerekir. Aksi `ErrorInfo` takdirde, başka bir taraf kendi sağlamadan bir hata üretirken nesne yanlışlıkla `ErrorInfo` kullanılabilir.

- Bir hatadan kaynaklanan tüm `HRESULT` yöntemlerin zengin hata bilgileri sağlamak <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> için yöntemini çağırması teşvik edilecektir. Döndürülen özel `HRESULT` bir hata `FACILITY_ITF` ise, uygun bir nesne sağlamak için yöntemi `ErrorInfo` gereklidir. Döndürülen hata standart bir sistem hatası ise (örneğin, , , , , ve gibi), açıkça yöntemini çağırmadan hata kodunun <xref:Microsoft.VisualStudio.VSConstants.E_OUTOFMEMORY> <xref:Microsoft.VisualStudio.VSConstants.E_ABORT> <xref:Microsoft.VisualStudio.VSConstants.E_INVALIDARG> <xref:Microsoft.VisualStudio.VSConstants.E_UNEXPECTED> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> döndürülebilir. Savunmaya yönelik bir kodlama stratejisi olarak, bir hata (sistem hataları dahil) kaynağı olarak, her zaman hatayı daha ayrıntılı bir şekilde açık bir şekilde açık olarak veya yöntemini `HRESULT` <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> `ErrorInfo` `null` arayın.

- Başka bir çağrıdan kaynaklanan bir hata döndürür tüm işlevler, nesnesini değiştirmeden içinde başarısız çağrısından `HRESULT` alınan bilgileri `ErrorInfo` iletir.

## <a name="see-also"></a>Ayrıca bkz.
- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>
- [SetErrorInfo (Bileşen Otomasyonu)](/previous-versions/windows/desktop/api/oleauto/nf-oleauto-seterrorinfo)
- [GetErrorInfo](/previous-versions/windows/desktop/api/oleauto/nf-oleauto-geterrorinfo)
- [ISupportErrorInfo Arabirimi](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-isupporterrorinfo)
