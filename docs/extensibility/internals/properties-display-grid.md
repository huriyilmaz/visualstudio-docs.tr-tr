---
title: Özellikler Ekran Izgara | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- properties [Visual Studio SDK], grid
ms.assetid: 318e41b0-acf5-4842-b85e-421c9d5927c5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d094c32ba8a64fc636f3fb6dfb2944dc3955628a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706183"
---
# <a name="properties-display-grid"></a>Özellikler görüntü ızgarası

**Özellikler** penceresi, ızgara içindeki alanları görüntüler. Sol sütunda özellik adları içerir; sağ sütun özellik değerlerini içerir.

## <a name="work-with-the-grid"></a>Izgara ile çalışma

İki sütunlu liste, tasarım zamanında değiştirilebilen yapılandırmadan bağımsız özellikleri ve geçerli ayarlarını gösterir. Tüm özelliklerin gösterilmeyebileceğini unutmayın. Bir özellik, örneğin, <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HideProperty%2A> yöntem uygulanarak gizli olarak ayarlanabilir. Özellikle, alt özelliklere sahip özellikleri gizlemek için:

1. Parametreyi `FALSE`' <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.DisplayChildProperties%2A> ye `pfDisplay` ayarlayın.

2. Parametreyi `TRUE`' <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HideProperty%2A> ye `pfHide` ayarlayın.

**Özellikleri** penceresine bilgi itmek için, <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>IDE kullanır. <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>**Özellikler** penceresinde görüntülenecek ilgili özelliklere sahip seçilebilir nesneler içeren her pencere için VSPackages tarafından çağrılır. **Çözüm Explorer**'ın <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> `GetProperty` __VSHPROPID kullanarak aramaların [uygulanması. ](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_BrowseObject>)VSHPROPID_BrowseObject proje hiyerarşinizde göz atılabilir nesneleri elde etmek için.

VSPackage'ınız __VSHPROPID [desteklemiyorsa. VSHPROPID_BrowseObject,](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_BrowseObject>)IDE __VSHPROPID <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> için değeri kullanarak kullanmaya [çalışır. ](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_SelContainer>)hiyerarşi öğesinin veya maddelerin tedarik ineVSHPROPID_SelContainer.

Projeniz VSPackage'ı oluşturması <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> gerekmez, çünkü bunu uygulayan IDE tarafından sağlanan pencere paketi (örneğin, **Çözüm Gezgini)** onun <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> adına oluşturur.

<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>IDE tarafından çağrılan üç yöntemden oluşur:

- <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.CountObjects%2A>**Özellikler** penceresinde görüntülenmek üzere seçilen nesne sayısını içerir.

- <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.GetObjects%2A>Özellikler `IDispatch` penceresinde görüntülenmek üzere seçilen nesneleri **Properties** döndürür.

- <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.SelectObjects%2A>döndürülen <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.GetObjects%2A> nesnelerden herhangi birinin kullanıcı tarafından seçilmesini mümkün kılar. Bu, VSPackage'ın Kullanıcı Yai'de kullanıcıya görüntülenen seçimi görsel olarak güncelleştirmesine olanak tanır.

**Özellikler** penceresi, göz atLanan özellikleri almak için `IDispatch` nesnelerden bilgi ayıklar. Özellikler tarayıcısı, nesneye hangi özellikleri desteklediğini `ITypeInfo`sorgulayarak sormak `IDispatch::GetTypeInfo`için kullanır `IDispatch` , hangisinden elde edilir. Tarayıcı daha sonra **Özellikler** penceresini doldurmak ve ızgarada görüntülenen tek tek özelliklerin değerlerini değiştirmek için bu değerleri kullanır. Özellikler bilgileri nesnenin kendi içinde tutulur.

Döndürülen nesneler destekverdiğinden, `IDispatch`arayan, istenen bilgileri temsil eden önceden `IDispatch::Invoke` `ITypeInfo::Invoke` tanımlanmış bir gönderi tanımlayıcısı (DISPID) ile arayarak nesnenin adı gibi bilgileri alabilir. Bildirilen DISPID'ler, kullanıcı tanımlı tanımlayıcılarla çakışmadığından emin olmak için negatiftir.

**Özellikler** penceresi, seçili bir nesnenin belirli özelliklerinin özelliklerine bağlı olarak farklı türde alanlar görüntüler. Bu alanlar, kutularını, açılır listelerini ve özel düzenleyici iletişim kutularına bağlantılar içerir.

- Numaralandırılmış bir listede yer alan değerler bir <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.GetObjects%2A> sorgu `IDispatch`tarafından alınır. Numaralandırılmış bir listeden elde edilen değerler, alan adını çift tıklatarak veya değere tıklayarak ve açılan listeden yeni değeri seçerek özellikler tablosunda değiştirilebilir. Numaralandırılmış listelerden önceden tanımlanmış ayarlara sahip özellikler için, Özellikler listesindeki özellik adını kullanılabilir seçenekler aracılığıyla çift tıklatma. True/false gibi yalnızca iki seçeneği olan önceden tanımlanmış özellikler için, seçenekler arasında geçiş yapmak için özellik adını çift tıklatın.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HasDefaultValue%2A> Eğer, `false`değerin değiştirildiğini gösteren ise, değer kalın metinde görüntülenir. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.CanResetPropertyValue%2A>değerin özgün değere sıfırlanıp sıfırlanamayacağına karar vermek için kullanılır. Bu nedenle, değere sağ tıklayarak ve görüntülenen menüden **Sıfırla'yı** seçerek varsayılan değere geri dönebilirsiniz. Aksi takdirde, değeri el ile varsayılana geri değiştirmeniz gerekir. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>ayrıca, tasarım süresi içinde görüntülenen özelliklerin adlarını yerelleştirmenize ve gizlemenize olanak tanır, ancak çalışma süresi sırasında görüntülenen özellik adlarını etkilemez.

- Elipsis (...) düğmesini tıklattığınızda, kullanıcının seçebileceği özellik değerlerinin bir listesi (renk seçici veya yazı tipi listesi gibi) görüntülenir. <xref:Microsoft.VisualStudio.Shell.Interop.IProvidePropertyBuilder>bu değerleri sağlar.

## <a name="see-also"></a>Ayrıca bkz.

- [Özellikleri genişletme](../../extensibility/internals/extending-properties.md)
