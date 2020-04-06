---
title: Hata İşleme ve İade Değerleri | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- errors [Visual Studio SDK], handling
- error handling
- return values
ms.assetid: b2d9079d-39a6-438a-8010-290056694b5c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 30b6b9bff9056360f9ea840f47b1488f05bee872
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711929"
---
# <a name="error-handling-and-return-values"></a>Hata işleme ve iade değerleri
VSPackages ve COM hatalar için aynı mimariyi kullanır. Ve `SetErrorInfo` `GetErrorInfo` işlevler Win32 uygulama programlama arabiriminin (API) bir parçasıdır. Tümleşik geliştirme ortamındaki (IDE) herhangi bir VSPackage, hata bildirimi alırken zengin hata bilgilerini kaydetmek için bu global Win32 API'lerini arayabilir. Hata [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] bilgilerini yönetmek için interop derlemeleri sağlar.

## <a name="interop-methods"></a>Interop yöntemleri
 Kolaylık sağlamak amacıyla, IDE Win32 API'lerini aramak yerine kullanmak üzere bir yöntem <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>sağlar. Yönetilen kod <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>kullanımında. Hata iletisinin görüntülenmesi gereken düzeye bir hata `HRESULT` geldiğinde (bu genellikle <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> komut işleyicisi uygulayan nesnedir), IDE uygun ileti kutusunu görüntülemek için başka bir yöntem <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A>kullanır. Yönetilen kodyöntemini <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> kullanın.

 VSPackage uygulayıcısı olarak, COM nesneleriniz `ISupportErrorInfo`normalde uygular. Arabirim, `ISupportErrorInfo` zengin hata bilgilerinin çağrı zincirinde dikey olarak hareket edebilmesini sağlar. İşlemler arasında veya iş parçacıkları arasında kullanılabilecek `ISupportErrorInfo` nesneler, zengin hata bilgilerinin arayana düzgün şekilde deftere kenekez indirilmesini sağlamak için desteklenmelidir.

 VSPackages ile ilgili olan ve editör fabrikaları, editörler, hiyerarşiler ve sunulan hizmetler de dahil olmak üzere IDE'nin genişletilmesinde rol oynayan tüm nesneler zengin hata bilgilerini desteklemelidir. IDE bu VSPackage nesnelerinin uygulanmasını `ISupportErrorInfo`gerektirmese de, her zaman teşvik edilir.

 IDE, hata bilgilerini bildirmekten ve bir ide'ye [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] `HRESULT` yayıldığında kullanıcıya görüntülemekten sorumludur. IDE aynı zamanda nesneleri `ErrorInfo` oluşturma mekanizmasıdır.

## <a name="general-guidelines"></a>Genel yönergeler
 VSPackage uygulamanızda dahilolan hataları ayarlamak ve bildirmek için de bu <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> yöntemleri <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> kullanabilirsiniz. Ancak, genel bir kural olarak, VSPackage'ınızda hata iletilerini işlemek için aşağıdaki yönergeleri izleyin:

- VSPackage COM nesnelerinizde uygulayın. `ISupportErrorInfo`

- Uygulayan nesnelerde <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> yöntemi çağıran bir hata raporlama <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>mekanizması oluşturun.

- IDE'nin yöntem aracılığıyla kullanıcılara hataları görüntülemesine <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> izin verin.

## <a name="error-information-in-the-ide"></a>IDE'deki hata bilgileri
 Aşağıdaki kurallar, IDE'deki hata [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] bilgilerinin nasıl işleyeceğini gösterir:

- Eski hata bilgisinin kullanıcılara bildirilmediğini garanti eden bir savunma <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> stratejisi olarak, <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> yöntemi arayan işlevler önce yöntemi aramalıdır. Yeni `null` hata bilgileri ayarlayabilecek herhangi bir şey aramadan önce önbelleğe alınmış hata iletilerini temizlemek için geçiş yap.

- Hata iletilerini doğrudan bildirmeyen işlevler yalnızca <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> bir hata `HRESULT`döndürmektedirlerse yöntemi arama izni verilir. Bir işleve `ErrorInfo` girişte veya geri dönerken açıklamak <xref:Microsoft.VisualStudio.VSConstants.S_OK>caizdir. Bu kuralın tek istisnası, bir `HRESULT` çağrının alıcı tarafın açıkça kurtarabileceği veya güvenli bir şekilde yoksayabileceği bir hatayı döndürür olmasıdır.

- Bir hatayı `HRESULT` açıkça yok sayan herhangi <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> bir <xref:Microsoft.VisualStudio.VSConstants.S_OK>taraf yöntemi ' yi ' ile çağırmalıdır. Aksi takdirde, `ErrorInfo` başka bir taraf kendi `ErrorInfo`hatası olmadan bir hata oluşturduğunda nesne yanlışlıkla kullanılabilir.

- Hata `HRESULT` dan kaynaklanan tüm yöntemler, zengin <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> hata bilgileri sağlamak için yöntemi çağırmak için teşvik edilir. Döndürülen `HRESULT` özel `FACILITY_ITF` bir hata ise, yöntem uygun `ErrorInfo`bir nesne sağlamak için gereklidir. Döndürülen hata standart bir sistem hatasıysa <xref:Microsoft.VisualStudio.VSConstants.E_OUTOFMEMORY> <xref:Microsoft.VisualStudio.VSConstants.E_ABORT>(örneğin, , , <xref:Microsoft.VisualStudio.VSConstants.E_INVALIDARG> <xref:Microsoft.VisualStudio.VSConstants.E_UNEXPECTED>, , vb.) <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> yöntemi açıkça aramadan hata kodunu döndürmek kabul edilebilir. Bir savunma kodlama stratejisi olarak, `HRESULT` bir hata (sistem hataları <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> dahil) kaynaklanırken, her zaman daha ayrıntılı olarak hata açıklayan, `ErrorInfo` ya `null`da yöntemi arayın.

- Başka bir çağrıyla kaynaklanan bir hatayı döndüren tüm işlevler, `HRESULT` `ErrorInfo` nesneyi değiştirmeden başarısız çağrıdan alınan bilgileri aktarmalıdır.

## <a name="see-also"></a>Ayrıca bkz.
- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>
- [SetErrorInfo (Bileşen Otomasyonu)](/previous-versions/windows/desktop/api/oleauto/nf-oleauto-seterrorinfo)
- [GetErrorInfo](/previous-versions/windows/desktop/api/oleauto/nf-oleauto-geterrorinfo)
- [ISupportErrorInfo Arayüzü](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-isupporterrorinfo)
