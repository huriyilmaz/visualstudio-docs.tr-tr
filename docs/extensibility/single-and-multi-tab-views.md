---
title: Tek ve Çok Sekmeli Görünümler | Microsoft Docs
description: Kod düzenleyicisi pencereleri ve form tasarımcısı gibi düzenleyicilerde çok sekmeli görünümlerin nasıl uygulandığını öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - single and multi-tab views
ms.assetid: e3611704-349f-4323-b03c-f2b0a445d781
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: d03563fe84d8985ab1fd1b746a05cd0c8d43e485
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126627254"
---
# <a name="single-and-multi-tab-views"></a>Tek ve Çoklu Sekme Görünümleri
Bir düzenleyici farklı görünüm türleri oluşturabilir. Örneklerden biri kod düzenleyicisi penceresi, diğeri ise form tasarımcısıdır.

 Çok sekmeli görünüm, birden çok sekme içeren bir görünümdir. Örneğin, HTML düzenleyicisinin en altında iki sekme vardır: **Tasarım** ve **Kaynak**, her biri mantıksal bir görünümdür. Tasarım görünümü işlenmiş bir web sayfasını, diğeri ise web sayfasını oluşturan HTML'yi görüntüler.

## <a name="accessing-physical-views"></a>Fiziksel Görünümlere Erişme
 Fiziksel görünümler, her biri kod veya form gibi arabellekte verilerin görünümünü temsil eden belge görünümü nesnelerini barındırabilir. Buna uygun olarak, her belge görünümü nesnesi bir fiziksel görünüme (fiziksel görünüm dizesi olarak bilinen bir şey tarafından tanımlanır) ve genellikle tek bir mantıksal görünüme sahiptir.

 Ancak bazı durumlarda fiziksel görünüm iki veya daha fazla mantıksal görünüme sahip olabilir. Bazı örnekler, yan yana görünümlere sahip bölünmüş pencereye sahip bir düzenleyici veya GUI/tasarım görünümü ve form görünümünün ardındaki koda sahip bir form tasarımcısıdır.

 Düzenleyicinizin tüm kullanılabilir fiziksel görünümlere erişmesini sağlamak için, düzenleyici fabrikanız tarafından oluşturula her belge görünümü nesnesi türü için benzersiz bir fiziksel görünüm dizesi oluşturmanız gerekir. Örneğin, düzenleyici [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] fabrikası bir kod penceresi ve form tasarımcısı penceresi için belge görünümü nesneleri oluşturabilir.

## <a name="creating-multi-tabbed-views"></a>Çok Sekmeli Görünümler Oluşturma
 Bir belge görünümü nesnesinin benzersiz bir fiziksel görünüm dizesi aracılığıyla fiziksel görünümle ilişkilendirilerek ilişkilendirilebilir, ancak verilerin farklı şekillerde görünümünü etkinleştirmek için fiziksel görünüme birden çok sekme ekleyebilirsiniz. Bu çok sekmeli yapılandırmada, tüm sekmeler aynı fiziksel görünüm dizesiyle ilişkilendirilse de her sekmeye farklı bir mantıksal görünüm GUID'si verilir.

 Bir düzenleyici için çok sekmeli bir görünüm oluşturmak için arabirimini gerçekleştirin ve ardından farklı bir mantıksal görünüm <xref:Microsoft.VisualStudio.Shell.Interop.IVsMultiViewDocumentView> GUID'si ( <xref:Microsoft.VisualStudio.Shell.Interop.LogicalViewID> ) ile, kendi oluştursanız her sekmeyle ilişkilendirilin.

 Html Visual Studio, çok sekmeli görünüme sahip bir düzenleyici örneğidir. Tasarım ve **Kaynak** **sekmeleri** vardır. Bunu etkinleştirmek için, tasarım sekmesi ve Kaynak sekmesi için her sekmeyle farklı bir `LOGICALVIEWID_TextView` mantıksal görünüm  `LOGICALVIEWID_Code` **ilişkilendirilr.**

 Uygun mantıksal görünümü belirterek VSPackage form tasarlama, kod düzenleme veya kodda hata ayıklama gibi belirli bir amaca karşılık gelen görünüme erişebilirsiniz. Ancak, pencerelerden biri NULL dizesiyle tanımlandı ve bu, birincil mantıksal görünüme ( ) karşılık gelebiliyor `LOGVIEWID_Primary` olmalıdır.

 Aşağıdaki tabloda, kullanılabilir mantıksal görünüm değerleri ve bunların kullanımı liste bulunmaktadır.

|LOGVIEWID GUID|Önerilen Kullanım|
|--------------------|---------------------|
|`LOGVIEWID_Primary`|Düzenleyici fabrikasının varsayılan/birincil görünümü.<br /><br /> Tüm düzenleyici fabrikaları bu değeri desteklemeli. Bu görünüm, fiziksel görünüm dizesi olarak NULL dizesini kullan olmalıdır. En az bir mantıksal görünümün bu değere ayarlanmış olması gerekir.|
|`LOGVIEWID_Debugging`|Hata ayıklama görünümü. Genellikle, `LOGVIEWID_Debugging` ile aynı görünüme eşler. `LOGVIEWID_Code`|
|`LOGVIEWID_Code`|Kodu Görüntüle komutu **tarafından başlatılan görünüm.**|
|`LOGVIEWID_Designer`|Formu Görüntüle komutu **tarafından başlatılan görünüm.**|
|`LOGVIEWID_TextView`|Metin düzenleyici görünümü. Bu, 'a erişen <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> bir görünüm döndüren görünümdir. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>|
|`LOGVIEWID_UserChooseView`|Kullanıcıdan hangi görünümün kullanmayacaklarını seçmesi istenir.|
|`LOGVIEWID_ProjectSpecificEditor`|Ile Aç **iletişim kutusu tarafından** şu şekilde geçirildi:<br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.OpenItem%2A><br /><br /> kullanıcı "(varsayılan düzenleyici Project" girişini seçer.|

 Mantıksal görünüm GUID'leri genişletilebilir olsa da, yalnızca VSPackage içinde tanımlanan mantıksal görünüm GUID'lerini kullanabilirsiniz.

 Kapatma sırasında Visual Studio düzenleyici fabrikasının GUID'sini ve belge penceresiyle ilişkili fiziksel görünüm dizelerini korur, böylece çözüm yeniden açıldığında belge pencerelerini yeniden açmak için kullanılabilir. Yalnızca çözüm kapatılan pencereler çözüm (.suo) dosyasında kalıcı olur. Bu değerler, `VSFPROPID_guidEditorType` yönteminde `VSFPROPID_pszPhysicalView` parametresinde geçirilen `propid` ve değerlerine <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> karşılık gelen değerlerdir.

## <a name="example"></a>Örnek
 Bu kod parçacığı, <xref:Microsoft.VisualStudio.Shell.Interop.LogicalViewID.TextView> nesnesinin uygulayan bir görünüme erişmek için nasıl kullanıldığını `IVsCodeWindow` gösterir. Bu durumda, hizmet <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShellOpenDocument> bir pencere çerçevesine işaretçi <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenDocumentViaProject%2A> alan çağrısı ve isteği için `LOGVIEWID_TextView` kullanılır. Belge görünümü nesnesine bir işaretçi çağrılarak ve <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> değeri belirterek elde `VSFPROPID_DocView` edilir. Belge görünümü nesnesinden için `QueryInterface` çağrılır. `IVsCodeWindow` Bu durumda bir metin düzenleyicisi döndürüldü ve bu nedenle yöntemde döndürülen belge görünümü nesnesi bir <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> kod penceresidir.

```cpp
HRESULT CFindTool::GotoFileLocation(const WCHAR * szFile, long iLine, long iStart, long iLen)
{
  HRESULT hr;
  if (NULL == szFile || !*szFile)
    return E_INVALIDARG;

  if (iLine == -1L)
    return S_FALSE;

  VSITEMID                  itemid;
  VARIANT                   var;
  RECT                      rc;
  IVsUIShellOpenDocument *  pOpenDoc    = NULL;
  IVsCodeWindow *           pCodeWin    = NULL;
  IVsTextView *             pTextView   = NULL;
  IVsUIHierarchy *          pHierarchy  = NULL;
  IVsWindowFrame *          pFrame      = NULL;
  IUnknown *                pUnk        = NULL;
  IVsHighlight *            pHighlight  = NULL;

  IfFailGo(CGlobalServiceProvider::HrQueryService(SID_SVsUIShellOpenDocument, IID_IVsUIShellOpenDocument, (void **)&pOpenDoc));
  IfFailGo(pOpenDoc->OpenDocumentViaProject(szFile, LOGVIEWID_TextView, NULL, &pHierarchy, &itemid, &pFrame));
  pFrame->Show();
  VariantInit(&var);
  IfFailGo(pFrame->GetProperty(VSFPROPID_DocView, &var));
  if (VT_UNKNOWN != var.vt) { hr = E_FAIL; goto Error; }
  pUnk = V_UNKNOWN(&var);
  if (NULL != pUnk)
  {
    IfFailGo(pUnk->QueryInterface(IID_IVsCodeWindow, (void **)&pCodeWin));
    if (SUCCEEDED(hr = pCodeWin->GetLastActiveView(&pTextView)) ||
        SUCCEEDED(hr = pCodeWin->GetPrimaryView(&pTextView)) )
    {
      pTextView->SetSelection(iLine, iStart, iLine, iStart + iLen);
      // uncover selection
      IfFailGo(pTextView->QueryInterface(IID_IVsHighlight, (void**)&pHighlight));
      IfFailGo(SUCCEEDED(pHighlight->GetHighlightRect(&rc)));
      UncoverSelectionRect(&rc);
    }
  }

Error:
  CLEARINTERFACE(pHighlight);
  CLEARINTERFACE(pTextView);
  CLEARINTERFACE(pCodeWin);
  CLEARINTERFACE(pUnk);
  CLEARINTERFACE(pFrame);
  CLEARINTERFACE(pOpenDoc);
  CLEARINTERFACE(pHierarchy);
  RedrawWindow(m_hwndResults, NULL, NULL, RDW_ERASE|RDW_FRAME|RDW_INVALIDATE|RDW_ALLCHILDREN);
  return hr;
}
```

## <a name="see-also"></a>Ayrıca bkz.
- [Birden Çok Belge Görünümünü Destekleme](../extensibility/supporting-multiple-document-views.md)
- [Nasıl Yapılır: Belge Verilerine Görünüm Ekleme](../extensibility/how-to-attach-views-to-document-data.md)
- [Özel Düzenleyiciler ve Tasarımcılar Oluşturma](../extensibility/creating-custom-editors-and-designers.md)
