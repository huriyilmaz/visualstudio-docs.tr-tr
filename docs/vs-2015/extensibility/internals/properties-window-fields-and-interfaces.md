---
title: Özellikler penceresi alanları ve arabirimleri | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Properties window, fields and interfaces
ms.assetid: 0328f0e5-2380-4a7a-a872-b547cb775050
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b58314d64536ecf33cc5589609ee5524a9352629
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65700819"
---
# <a name="properties-window-fields-and-interfaces"></a>Özellikler Penceresi Alanları ve Arabirimleri
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

**Özellikler** penceresinde hangi bilgilerin görüntülendiğini belirlemek için seçim MODELI, IDE 'ye odaklanılmış pencereyi temel alır. Seçili penceredeki her pencere ve nesnenin seçim bağlamı nesnesi genel seçim bağlamına itilmiş olabilir. Bu pencere odağa sahip olduğunda, ortam, genel seçim bağlamını bir pencere çerçevesindeki değerlerle güncelleştirir. Odak değiştiğinde seçim bağlamını de yapar.  
  
## <a name="tracking-selection-in-the-ide"></a>IDE 'de seçimi izleme  
 IDE 'nin sahip olduğu pencere çerçevesinin veya sitenin adlı bir hizmeti vardır <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> . Aşağıdaki adımlarda, bir seçimdeki değişikliğin, kullanıcının odağı başka bir açık pencereye değiştirme veya **Çözüm Gezgini**' de farklı bir proje öğesi seçme, **Özellikler** penceresinde görüntüleneni değiştirmek için uygulanıp uygulanmadığı gösterilmektedir.  
  
1. Seçili pencerede yer alan VSPackage tarafından oluşturulan nesne <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A> Invoke sahibi olacak şekilde çağırır <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection> .  
  
2. Seçilen pencere tarafından sunulan seçim kapsayıcısı kendi <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> nesnesini oluşturur. Seçim değiştiğinde VSPackage, <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> değişikliğin **Özellikler** penceresi dahil olmak üzere ortamdaki tüm dinleyicileri bilgilendirmek için çağırır. Ayrıca, yeni seçimle ilgili hiyerarşi ve öğe bilgilerine erişim sağlar.  
  
3. <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A>' In seçili hiyerarşi öğeleri çağrısı ve geçirilmesi, `VSHPROPID_BrowseObject` <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> nesneyi doldurur.  
  
4. [IDispatch arabiriminden](https://msdn.microsoft.com/ebbff4bc-36b2-4861-9efa-ffa45e013eb5) türetilmiş bir nesne <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> , istenen öğe için döndürülür ve ortam onu bir <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> (bkz. aşağıdaki adıma). Çağrı başarısız olursa, ortam için ikinci bir çağrı yapılır `IVsHierarchy::GetProperty` , bu da <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> hiyerarşi öğesi veya öğelerin tedariki olan seçim kapsayıcısını geçiyor.  
  
    <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>Ortam tarafından sağlanan Window VSPackage, onun adına (örneğin, **Çözüm Gezgini**) yapılarını kullandığından, projeniz VSPackage oluşturmaz <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> .  
  
5. Ortam, <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> `IDispatch` **Özellikler** penceresini dolduracak arabirimi temel alan nesneleri almak için yöntemlerini çağırır.  
  
   **Properties** penceresindeki bir değer değiştirildiğinde VSPackages, `IVsTrackSelectionEx::OnElementValueChangeEx` `IVsTrackSelectionEx::OnSelectionChangeEx` değişikliği öğe değerine bildirmek için ve öğesini uygular. Daha sonra ortam, <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> **Özellikler** penceresinde görüntülenecek bilgileri özellik değerleriyle eşitlenmiş halde tutmak için veya öğesini çağırır. Daha fazla bilgi için bkz. [Özellikler penceresinde özellik değerlerini güncelleştirme](../../misc/updating-property-values-in-the-properties-window.md).  
  
   Bu öğeyle ilgili özellikleri göstermek için **Çözüm Gezgini** içinde farklı bir proje öğesi seçmeye ek olarak, **Özellikler** penceresinde bulunan açılan listeyi kullanarak form veya belge penceresi içinden farklı bir nesne de seçebilirsiniz. Daha fazla bilgi için bkz. [Özellikler penceresi nesne listesi](../../extensibility/internals/properties-window-object-list.md).  
  
   **Özellikler** penceresi kılavuzunda, bilgilerin gösterildiği biçimi alfabetik olarak kategorilere göre değiştirebilirsiniz ve varsa, **Özellikler** penceresindeki ilgili düğmelere tıklayarak seçili bir nesne için bir özellik sayfası da açabilirsiniz. Daha fazla bilgi için bkz. [Özellikler penceresi düğmeleri](../../extensibility/internals/properties-window-buttons.md) ve [Özellik sayfaları](../../extensibility/internals/property-pages.md).  
  
   Son olarak, **Özellikler** penceresinin alt kısmında **Özellikler** penceresi kılavuzunda seçilen alanın bir açıklaması da bulunur. Daha fazla bilgi için bkz. [Özellikler penceresinden alan açıklamalarını alma](../../misc/getting-field-descriptions-from-the-properties-window.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Özellikleri Genişletme](../../extensibility/internals/extending-properties.md)
