---
title: Özellikler görüntü Kılavuzu | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80706183"
---
# <a name="properties-display-grid"></a>Özellikler görüntü Kılavuzu

**Özellikler** penceresi kılavuz içindeki alanları görüntüler. Sol sütun özellik adlarını içerir; sağ sütun, özellik değerlerini içerir.

## <a name="work-with-the-grid"></a>Kılavuzla çalışma

İki sütunlu liste, tasarım zamanında değiştirilebilen yapılandırmaya bağımsız özellikleri ve bunların geçerli ayarlarını gösterir. Tüm özelliklerin gösterilmediğini unutmayın. Bir özellik, örneğin, yöntemi uygulayarak gizli olarak ayarlanabilir <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HideProperty%2A> . Özellikle, alt özellikleri olan özellikleri gizlemek için:

1. `pfDisplay`Parametresini <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.DisplayChildProperties%2A> olarak ayarlayın `FALSE` .

2. `pfHide`Parametresini <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HideProperty%2A> olarak ayarlayın `TRUE` .

**Özellikler** penceresine bilgi göndermek için IDE 'yi kullanır <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> . <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> , **Özellikler** penceresinde görüntülenecek ilgili özelliklerle birlikte seçilebilir nesneler içeren her bir pencere Için VSPackages tarafından çağırılır. **Çözüm Gezgini**, <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> __VSHPROPID kullanılarak yapılan çağrıların uygulanması `GetProperty` [. ](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_BrowseObject>) Browseable nesnelerini hiyerarşide almak için proje hiyerarşinizdeki VSHPROPID_BrowseObject.

VSPackage [__VSHPROPID desteklemiyorsa. VSHPROPID_BrowseObject](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_BrowseObject>), ıde <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> __VSHPROPID değerini kullanarak kullanmaya çalışır [. ](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_SelContainer>) Hiyerarşi öğesi veya öğelerinin tedarik VSHPROPID_SelContainer.

Proje VSPackage 'ın, <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> kendi adına UYGULADıĞı IDE tarafından sağlanan pencere paketi (örneğin, **Çözüm Gezgini**) oluşturduğundan oluşturulması gerekmez <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> .

<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> IDE tarafından çağrılan üç yöntemden oluşur:

- <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.CountObjects%2A>**Özellikler** penceresinde görüntülenmek üzere seçilen nesne sayısını içerir.

- <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.GetObjects%2A>`IDispatch` **Özellikler** penceresinde görüntülenmek üzere seçilen nesneleri döndürür.

- <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.SelectObjects%2A> tarafından döndürülen nesnelerden herhangi birinin <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.GetObjects%2A> Kullanıcı tarafından seçilebilmesini sağlar. Bu, VSPackage 'ın Kullanıcı ARABIRIMINDEKI kullanıcıya görüntülenecek seçimi görsel olarak güncelleştirmesine olanak sağlar.

**Özellikler** penceresi, `IDispatch` gözatılan özellikleri almak için nesnelerdeki bilgileri ayıklar. Özellikler tarayıcısı, `IDispatch` `ITypeInfo` ' den elde edilen sorgulama yaparak nesne tarafından desteklenen özellikleri ister `IDispatch::GetTypeInfo` . Daha sonra tarayıcı, **Özellikler** penceresini doldurmak ve kılavuzda görüntülenecek ayrı özellikler için değerleri değiştirmek üzere bu değerleri kullanır. Özellikler bilgisi nesnenin kendisi içinde tutulur.

Döndürülen nesneler desteklediği için `IDispatch` çağıran, `IDispatch::Invoke` `ITypeInfo::Invoke` istenen bilgileri temsil eden önceden tanımlanmış bir dağıtım tanımlayıcısı (DISPID) ile ya da çağırarak nesne adı gibi bilgileri elde edebilir. Kullanıcı tanımlı tanımlayıcılarla çakışmadıklarından emin olmak için, tanımlanan DISPID 'ler negatif.

**Özellikler** penceresi, seçilen bir nesnenin belirli özelliklerinin özniteliklerine bağlı olarak farklı türlerdeki alanları görüntüler. Bu alanlar düzenleme kutularını, açılan listeleri ve özel Düzenleyici iletişim kutularına bağlantıları içerir.

- Numaralandırılmış bir listede yer alan değerler bir sorgu tarafından alınır <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.GetObjects%2A> `IDispatch` . Numaralandırılmış bir listeden alınan değerler, alan adına çift tıklayarak ya da değere tıklayıp açılan listeden yeni değer seçilerek Özellikler kılavuzunda değiştirilebilir. Numaralandırılmış listelerden önceden tanımlanmış ayarlara sahip özellikler için, Özellikler listesinde özellik adına çift tıklamak, kullanılabilir seçimler aracılığıyla geçiş yapar. Yalnızca iki seçenekli (true/false gibi) önceden tanımlanmış özellikler için, seçenekler arasında geçiş yapmak üzere özellik adına çift tıklayın.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HasDefaultValue%2A>İse, `false` değerin değiştirildiğini belirten değer kalın metinde görüntülenir. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.CanResetPropertyValue%2A> değerin özgün değere sıfırlanıp sıfırlanmadığını anlamak için kullanılır. Bu durumda, değere sağ tıklayıp görüntülenecek menüden **Sıfırla** ' yı seçerek varsayılana geri dönebilirsiniz. Aksi takdirde, değeri el ile varsayılan olarak değiştirmeniz gerekir. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing> Ayrıca tasarım zamanı sırasında görüntülene Özellikler adlarını yerelleştirebilmeniz ve gizlemenize izin verir, ancak çalışma zamanı sırasında görüntülenecek özellik adlarını etkilemez.

- Üç nokta (...) düğmesine tıklamak, kullanıcının seçebileceğiniz özellik değerlerinin bir listesini görüntüler (bir renk seçici veya yazı tipi listesi gibi). <xref:Microsoft.VisualStudio.Shell.Interop.IProvidePropertyBuilder> Bu değerleri sağlar.

## <a name="see-also"></a>Ayrıca bkz.

- [Özellikleri Genişlet](../../extensibility/internals/extending-properties.md)
