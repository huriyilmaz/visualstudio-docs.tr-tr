---
title: Tek ve Çoklu Sekmeli Görünümler | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - single and multi-tab views
ms.assetid: e3611704-349f-4323-b03c-f2b0a445d781
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c308b4d6c7b90456255019ef57c6b9d544aefc77
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699985"
---
# <a name="single-and-multi-tab-views"></a>Tek ve Çoklu Sekme Görünümleri
Bir düzenleyici farklı görünüm türleri oluşturabilir. Bir örnek bir kod düzenleyicisi penceresi, başka bir form tasarımcısı.

 Çok sekmeli görünüm, birden çok sekme olan bir görünümdür. Örneğin, HTML düzenleyicisinin alt kısmında iki sekme vardır: **Tasarım** ve **Kaynak,** her biri mantıksal bir görünüm. Tasarım görünümü işlenmiş bir web sayfasını görüntülerken, diğer sayfa web sayfasını oluşturan HTML'yi görüntüler.

## <a name="accessing-physical-views"></a>Fiziksel Görünümler'e Erişim
 Fiziksel görünümler, her biri arabellekteki kod veya form gibi veri görünümünü temsil eden belge görünümü nesnelerini barındırıyor. Buna göre, her belge görünümü nesnesi fiziksel bir görünüme (fiziksel görünüm dizesi olarak bilinen bir şey tarafından tanımlanan) ve genellikle tek bir mantıksal görünüme sahiptir.

 Ancak bazı durumlarda, fiziksel bir görünüm iki veya daha fazla mantıksal görünüme sahip olabilir. Bazı örnekler, yan yana görünümleri olan bölünmüş penceresi olan bir düzenleyici veya GUI/tasarım görünümü ve form un arkasında kod görünümü olan form tasarımcısıdır.

 Düzenleyicinizin kullanılabilir tüm fiziksel görünümlere erişmesini sağlamak için, düzenleyici fabrikanızın oluşturabileceği her belge görünümü nesnesi türü için benzersiz bir fiziksel görünüm dizesi oluşturmanız gerekir. Örneğin, [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] düzenleyici fabrika bir kod penceresi ve formlar tasarımcısı penceresi için belge görünümü nesneleri oluşturabilirsiniz.

## <a name="creating-multi-tabbed-views"></a>Çok Sekmeli Görünümler Oluşturma
 Belge görünümü nesnesi benzersiz bir fiziksel görünüm dizesi aracılığıyla fiziksel görünümle ilişkilendirilmesi gerekirken, verilerin farklı şekillerde görüntülenmesini etkinleştirmek için fiziksel görünüme birden çok sekme yerleştirebilirsiniz. Bu çok sekmeli yapılandırmada, tüm sekmeler aynı fiziksel görünüm dizesiyle ilişkilidir, ancak her sekmefarklı bir mantıksal görünüm GUID verilir.

 Bir düzenleyici için çok sekmeli görünüm oluşturmak <xref:Microsoft.VisualStudio.Shell.Interop.IVsMultiViewDocumentView> için arabirimi uygulayın ve<xref:Microsoft.VisualStudio.Shell.Interop.LogicalViewID>ardından oluşturduğunuz her sekmeyle farklı bir mantıksal görünüm GUID ( ) ilişkilendirin.

 Visual Studio HTML düzenleyicisi, çok sekmeli görünümü olan bir düzenleyici örneğidir. **Tasarım** ve **Kaynak** sekmeleri vardır. Bunu etkinleştirmek için, **Tasarım** sekmesi ve `LOGICALVIEWID_Code` `LOGICALVIEWID_TextView` **Kaynak** sekmesi için her sekmeyle farklı bir mantıksal görünüm ilişkilidir.

 Uygun mantıksal görünümü belirterek, VSPackage form tasarlama, kod düzenleme veya hata ayıklama kodu gibi belirli bir amaca karşılık gelen görünüme erişebilir. Ancak, pencerelerden biri NULL dizesi tarafından tanımlanmalıdır ve bu`LOGVIEWID_Primary`birincil mantıksal görünüme karşılık getirmelidir ( ).

 Aşağıdaki tabloda kullanılabilir mantıksal görünüm değerleri ve bunların kullanımı listelenmektedir.

|LOGVIEWID REHBER|Önerilen Kullanım|
|--------------------|---------------------|
|`LOGVIEWID_Primary`|Düzenleyici fabrikasının varsayılan/birincil görünümü.<br /><br /> Tüm editör fabrikaları bu değeri desteklemelidir. Bu görünüm, null dizesini fiziksel görünüm dizesi olarak kullanmalıdır. En az bir mantıksal görünüm bu değere ayarlanmalıdır.|
|`LOGVIEWID_Debugging`|Hata ayıklama görünümü. Genellikle, `LOGVIEWID_Debugging` eşler aynı görünüme `LOGVIEWID_Code`.|
|`LOGVIEWID_Code`|Görünüm Kodu komutu tarafından başlatılan **görünüm.**|
|`LOGVIEWID_Designer`|Görünüm Formu komutu tarafından başlatılan **görünüm.**|
|`LOGVIEWID_TextView`|Metin editörü görünümü. Bu, erişebileceğiniz <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>döndüren görünümdür.|
|`LOGVIEWID_UserChooseView`|Kullanıcıdan hangi görünümün kullanılacağını seçmesini ister.|
|`LOGVIEWID_ProjectSpecificEditor`|**İletişim kutusuyla Aç'ın** yanından geçerek<br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.OpenItem%2A><br /><br /> kullanıcı "(Project varsayılan düzenleyicisi)" girişini seçtiğinde.|

 Mantıksal görünüm GUID'leri genişletilebilir olsa da, yalnızca VSPackage'ınızda tanımlanan mantıksal görünüm GUID'lerini kullanabilirsiniz.

 Kapatma da Visual Studio, çözüm yeniden açıldığında belge pencerelerini yeniden açmak için kullanılabilmek için düzenleyici fabrikasının GUID'ini ve belge penceresiyle ilişkili fiziksel görünüm dizelerini korur. Yalnızca çözüm kapatıldığında açık olan pencereler çözüm (.suo) dosyasında kalıcıdır. Bu `VSFPROPID_guidEditorType` değerler `VSFPROPID_pszPhysicalView` `propid` <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> yöntemde parametrede geçen değerlere karşılık gelir.

## <a name="example"></a>Örnek
 Bu snippet, nesnenin <xref:Microsoft.VisualStudio.Shell.Interop.LogicalViewID.TextView> uygulayan bir görünüme erişmek `IVsCodeWindow`için nasıl kullanıldığını gösterir. Bu durumda, <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShellOpenDocument> hizmet aramak <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenDocumentViaProject%2A> ve istemek `LOGVIEWID_TextView`için kullanılır , hangi bir pencere çerçevesi için bir işaretçi alır. Belge görünümü nesnesine işaretçi çağırılarak <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> ve `VSFPROPID_DocView`bir değer belirterek elde edilir. Belge görünümü nesnesinden, `QueryInterface` çağrılır. `IVsCodeWindow` Bu durumda beklenti bir metin düzenleyicisi döndürülür ve bu nedenle <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> yöntemde döndürülen belge görünümü nesnesi bir kod penceresi olmasıdır.

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
