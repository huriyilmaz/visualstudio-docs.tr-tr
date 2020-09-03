---
title: Eski API 'YI kullanarak görünüm ayarlarını değiştirme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - changing view settings
ms.assetid: 12c9b300-0894-4124-96a1-764326176d77
caps.latest.revision: 19
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a7d58d1477b9d7f58242f8cb4db7c3c360c248b9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68184472"
---
# <a name="changing-view-settings-by-using-the-legacy-api"></a>Eski API'yi Kullanarak Görünüm Ayarlarını Değiştirme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sözcük kaydırması, seçim kenar boşluğu ve sanal alan gibi çekirdek Düzenleyici özellikleri için ayarlar, **Seçenekler** iletişim kutusu aracılığıyla Kullanıcı tarafından değiştirilebilir. Ancak, bu ayarları program aracılığıyla değiştirmek de mümkündür.  
  
## <a name="changing-settings-by-using-the-legacy-api"></a>Eski API 'YI kullanarak ayarları değiştirme  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer>Arabirim bir metin Düzenleyicisi özellikleri kümesi sunar. Metin görünümü, metin görünümü için programlı olarak değiştirilen ayarların grubunu temsil eden bir özellikler kategorisi (GUID_EditPropCategory_View_MasterSettings) içerir. Görünüm ayarları bu şekilde değiştirildikten sonra, bunlar sıfırlanana kadar **Seçenekler** iletişim kutusunda değiştirilemez.  
  
 Aşağıda, bir çekirdek Düzenleyicisi örneğinin görünüm ayarlarını değiştirmek için tipik bir işlem verilmiştir.  
  
1. `QueryInterface` <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> Arabirimi için () çağırın <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer> .  
  
2. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer.GetPropertyCategory%2A>Parametresi için bir GUID_EditPropCategory_View_MasterSettings değeri belirterek yöntemi çağırın `rguidCategory` .  
  
     Bunu yapmak, bu, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer> görünüm için zorlanan özellikler kümesini içeren arabirime bir işaretçi döndürür. Bu gruptaki tüm ayarlar kalıcı olarak zorlanır. Bir ayar bu grupta değilse, **Seçenekler** iletişim kutusunda veya Kullanıcı komutlarında belirtilen seçenekleri takip eder.  
  
3. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.SetProperty%2A>Parametresinde uygun ayarlar değerini belirterek yöntemi çağırın `idprop` .  
  
     Örneğin, sözcük kaydırmayı zorlamak için, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.SetProperty%2A> parametresi için VSEDITPROPID_ViewLangOpt_WordWrap değerini çağırın ve bir değer belirtin `vt` `idprop` . Bu çağrıda `vt` VT_BOOL türünde BIR değişkendir ve `vt.boolVal` VARIANT_TRUE.  
  
## <a name="resetting-changed-view-settings"></a>Değiştirilen görünüm ayarlarını sıfırlama  
 Çekirdek düzenleyicinin bir örneği için değiştirilen görünüm ayarlarını sıfırlamak için, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.RemoveProperty%2A> yöntemini çağırın ve parametresinde uygun ayar değerini belirtin `idprop` .  
  
 Örneğin, sözcük kaydırma özelliğinin serbestçe kaydırılmasına izin vermek için, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.RemoveProperty%2A> parametre için bir VSEDITPROPID_ViewLangOpt_WordWrap değeri çağırarak ve belirterek Özellik kategorisinden kaldırılır `idprop` .  
  
 Çekirdek düzenleyicinin tüm değiştirilen ayarlarını aynı anda kaldırmak için, parametre için bir VSEDITPROPID_ViewComposite_AllCodeWindowDefaults, VT değeri belirtin `idprop` . Bu çağrıda, VT VT_BOOL ve VT. boolVal VARIANT_TRUE türünde bir DEĞIŞKENDIR.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Çekirdek düzenleyicinin içinde](../extensibility/inside-the-core-editor.md)   
 [Eski API kullanarak metin görünümüne erişme](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)   
 [Seçenekler Iletişim kutusu](../ide/reference/options-dialog-box-visual-studio.md)
