---
title: Hata Işleme ve dönüş değerleri | Microsoft Docs
description: Visual Studio SDK 'nın bir hata bildirimi alırken zengin hata bilgilerini kaydetmek için birlikte çalışma derlemeleri nasıl sağladığını öğrenin.
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
ms.workload:
- vssdk
ms.openlocfilehash: ef33936e3dc36d98cc88b1285aa0b198a84cbd59
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112898327"
---
# <a name="error-handling-and-return-values"></a>Hata işleme ve dönüş değerleri
VSPackages ve COM, hatalar için aynı mimariyi kullanır. `SetErrorInfo`Ve `GetErrorInfo` Işlevleri, Win32 uygulama programlama ARABIRIMININ (API) bir parçasıdır. Tümleşik geliştirme ortamındaki (IDE) herhangi bir VSPackage, hata bildirimi alırken zengin hata bilgilerini kaydetmek için bu genel Win32 API 'Lerini çağırabilir. , [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] Hata bilgilerini yönetmek için birlikte çalışma derlemeleri sağlar.

## <a name="interop-methods"></a>Birlikte çalışma yöntemleri
 Bir kolaylık olması halinde, IDE, <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> Win32 API 'lerini çağırmak yerine kullanmak için bir yöntem sağlar. Yönetilen kod kullanımı <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> . `HRESULT`Hata iletisinin gösterilmesi gereken düzeye bir hata ulaştığında (Bu genellikle bir <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> komut işleyicisini uygulayan nesnedir), IDE, <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> uygun ileti kutusunu göstermek için başka bir yöntem kullanır. Yönetilen kodda <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> yöntemini kullanın.

 VSPackage uygulayıcısı olarak COM nesneleriniz normalde uygular `ISupportErrorInfo` . `ISupportErrorInfo`Arabirim, zengin hata bilgilerinin, çağrı zincirinde dikey olarak taşınmasını sağlar. İşlem genelinde veya iş parçacıkları genelinde kullanılabilecek nesneler, `ISupportErrorInfo` zengin hata bilgilerinin çağırana doğru şekilde geri sıralandığından emin olmak için desteklemelidir.

 VSPackages ile ilgili olan ve düzenleyici fabrikası, düzenleyiciler, hiyerarşiler ve sunulan hizmetler de dahil olmak üzere IDE 'yi genişletmeye dahil olan tüm nesneler, zengin hata bilgilerini desteklemelidir. IDE, bu VSPackage nesnelerinin uygulanmasını gerektirse de `ISupportErrorInfo` her zaman önerilir.

 IDE, hata bilgilerini bildirmekten ve [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE 'ye her yayıldıktan sonra bir kullanıcıya görüntülüyor `HRESULT` . IDE, nesne oluşturmaya yönelik mekanizmaya de sahiptir `ErrorInfo` .

## <a name="general-guidelines"></a>Genel yönergeler
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>Ve <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> yöntemlerini, VSPackage uygulamanızda iç hataları ayarlamak ve raporlamak için de kullanabilirsiniz. Bununla birlikte, genel bir kural olarak, VSPackage 'daki hata iletilerini işlemek için aşağıdaki yönergeleri izleyin:

- `ISupportErrorInfo`VSPackage com nesnelerinizi uygulayın.

- Uygulayan nesnelerde yöntemini çağıran bir hata raporlama mekanizması oluşturun <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> .

- IDE 'nin yöntemi aracılığıyla kullanıcılara hata görüntülemesine izin verin <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> .

## <a name="error-information-in-the-ide"></a>IDE 'de hata bilgileri
 Aşağıdaki kurallar IDE 'de hata bilgilerinin nasıl işleneceğini gösterir [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] :

- Eski hata bilgilerinin kullanıcılara bildirilmediğinden emin olmak için savunma stratejisi olarak, yöntemi çağıran işlevler <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> öncelikle <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> yöntemi çağırmalıdır. `null`Yeni hata bilgileri ayarlayabilen herhangi bir şeyi çağırmadan önce önbelleğe alınmış hata iletilerini temizlemek için geçirin.

- Doğrudan hata iletilerini bildirmeyen işlevlerin yalnızca <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> bir hata döndürmeleri durumunda yöntemi çağırması için izin verilir `HRESULT` . `ErrorInfo`Girişi bir işleve veya döndürme sırasında temizlemek için izin verilir <xref:Microsoft.VisualStudio.VSConstants.S_OK> . Bu kuralın tek istisnası, bir çağrının, `HRESULT` alıcı tarafın açıkça kurtarabileceği veya güvenli bir şekilde yoksaydığı bir hata döndürdüğü durumdur.

- Açıkça bir hatayı yok sayan herhangi bir tarafın `HRESULT` <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> ile yöntemini çağırması gerekir <xref:Microsoft.VisualStudio.VSConstants.S_OK> . Aksi takdirde, `ErrorInfo` nesne yanlışlıkla başka bir taraf kendi kendine sağlamadan bir hata oluşturduğunda kullanılıyor olabilir `ErrorInfo` .

- Bir hata oluşturan tüm yöntemlerin `HRESULT` <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> zengin hata bilgileri sağlamak için yöntemini çağırması önerilir. Döndürülen `HRESULT` özel bir `FACILITY_ITF` hata ise, uygun bir nesne sağlamak için yöntemi gerekir `ErrorInfo` . Döndürülen hata standart sistem hatası ise (örneğin,,,, vb <xref:Microsoft.VisualStudio.VSConstants.E_OUTOFMEMORY> <xref:Microsoft.VisualStudio.VSConstants.E_ABORT> <xref:Microsoft.VisualStudio.VSConstants.E_INVALIDARG> <xref:Microsoft.VisualStudio.VSConstants.E_UNEXPECTED> .), yöntemi açıkça çağrılmadan hata kodunu döndürmek kabul edilebilir <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> . Bir hata oluştuğunda (sistem hataları dahil) Savunma kod oluşturma stratejisi olarak, hatayı `HRESULT` <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> `ErrorInfo` daha ayrıntılı olarak açıklayan veya ya da yöntemini her zaman çağırın `null` .

- Başka bir çağrının kaynaklandığı bir hatayı döndüren tüm işlevler, nesne üzerinde değişiklik yapmadan, içindeki başarısız çağrıdan alınan bilgileri iletmelidir `HRESULT` `ErrorInfo` .

## <a name="see-also"></a>Ayrıca bkz.
- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>
- [SetErrorInfo (Bileşen Otomasyonu)](/previous-versions/windows/desktop/api/oleauto/nf-oleauto-seterrorinfo)
- [GetErrorInfo](/previous-versions/windows/desktop/api/oleauto/nf-oleauto-geterrorinfo)
- [Iupporterrorınfo arabirimi](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-isupporterrorinfo)
