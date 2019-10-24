---
title: Tek ve çok sekme görünümleri | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - single and multi-tab views
ms.assetid: e3611704-349f-4323-b03c-f2b0a445d781
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c651bda042524b2ed3188fef880f848bb0087433
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72720069"
---
# <a name="single-and-multi-tab-views"></a>Tek ve Çoklu Sekme Görünümleri
Bir düzenleyici, farklı türlerde görünümler oluşturabilir. Bir örnek, bir kod Düzenleyicisi penceresidir, diğeri ise form tasarlayıcıdır.

 Çok sekmeli Görünüm, birden çok sekmeye sahip bir görünümdir. Örneğin, HTML Düzenleyicisi alt kısımdaki iki sekmeye sahiptir: **Tasarım** ve **kaynak**, her bir mantıksal görünüm. Tasarım görünümü işlenmiş bir Web sayfasını görüntüler, diğer bir deyişle, Web sayfasından oluşan HTML 'yi görüntüler.

## <a name="accessing-physical-views"></a>Fiziksel görünümlere erişme
 Fiziksel görünümler, her biri arabellekteki verilerin bir görünümünü temsil eden (örneğin, kod veya form) belge görünümü nesnelerini barındırır. Buna uygun olarak, her belge görünümü nesnesinin fiziksel bir görünümü vardır (fiziksel görünüm dizesi olarak bilinen bir öğe tarafından tanımlanır) ve genellikle tek bir mantıksal görünüm.

 Ancak, bazı durumlarda, fiziksel bir görünüm iki veya daha fazla mantıksal görünüme sahip olabilir. Yan yana görünümleri olan bölünmüş bir pencere veya GUI/tasarım görünümü ve bir arka plan kod görünümü içeren bir form Tasarımcısı içeren bir düzenleyici, bazı örneklerdir.

 Düzenleyicinizi kullanılabilir tüm fiziksel görünümlere erişecek şekilde etkinleştirmek için, Düzenleyici fabrikanızın oluşturabileceğiniz her belge görünümü nesnesi türü için benzersiz bir fiziksel görünüm dizesi oluşturmanız gerekir. Örneğin, [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] Düzenleyicisi fabrikası, bir kod penceresi ve bir form Tasarımcısı penceresi için belge görünümü nesneleri oluşturabilir.

## <a name="creating-multi-tabbed-views"></a>Çok sekmeli görünümler oluşturma
 Bir belge görünümü nesnesinin benzersiz bir fiziksel görünüm dizesi aracılığıyla fiziksel bir görünümle ilişkilendirilmesi gerekir, ancak verilerin farklı yollarla görüntülenmesini sağlamak için fiziksel görünümün içine birden çok sekme yerleştirebilirsiniz. Bu çok sekmeli yapılandırmada, tüm sekmeler aynı fiziksel görünüm dizesiyle ilişkilendirilir, ancak her sekmeye farklı bir mantıksal görünüm GUID 'SI verilir.

 Bir düzenleyici için çok sekmeli bir görünüm oluşturmak üzere <xref:Microsoft.VisualStudio.Shell.Interop.IVsMultiViewDocumentView> arabirimini uygulayın ve ardından oluşturduğunuz her sekmeden farklı bir mantıksal görünüm GUID 'SI (<xref:Microsoft.VisualStudio.Shell.Interop.LogicalViewID>) ilişkilendirin.

 Visual Studio HTML Düzenleyicisi, çok sekmeli Görünüm içeren bir düzenleyiciye örnektir. **Tasarım** ve **kaynak** sekmeleri vardır. Bunu etkinleştirmek için, farklı bir mantıksal görünüm her sekme ile ilişkilendirilir, **Tasarım** sekmesi için `LOGICALVIEWID_TextView` ve **kaynak** sekmesi için `LOGICALVIEWID_Code`.

 Uygun mantıksal görünümü belirterek, bir VSPackage, form tasarlama, kod düzenlemesi veya hata ayıklama kodu gibi belirli bir amaca karşılık gelen görünüme erişebilir. Ancak, bir Windows, NULL dize ile tanımlanmalıdır ve bunun birincil mantıksal görünüme (`LOGVIEWID_Primary`) karşılık gelmesi gerekir.

 Aşağıdaki tabloda kullanılabilir mantıksal görünüm değerleri ve kullanımları listelenmektedir.

|LOGVIEıD GUID|Önerilen kullanım|
|--------------------|---------------------|
|`LOGVIEWID_Primary`|Düzenleyici fabrikasının varsayılan/birincil görünümü.<br /><br /> Tüm Düzenleyici fabrikaları bu değeri desteklemelidir. Bu görünümün fiziksel görünüm dizesi olarak NULL dize kullanması gerekir. En az bir mantıksal görünüm bu değere ayarlanmalıdır.|
|`LOGVIEWID_Debugging`|Hata ayıklama görünümü. Genellikle, `LOGVIEWID_Debugging` `LOGVIEWID_Code`ile aynı görünüme eşlenir.|
|`LOGVIEWID_Code`|Görünüm **kodu** komutuyla başlatılan görünüm.|
|`LOGVIEWID_Designer`|Görünüm **formu** komutuyla başlatılan görünüm.|
|`LOGVIEWID_TextView`|Metin düzenleyici görünümü. Bu, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>erişebileceğiniz <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>döndüren görünümüdür.|
|`LOGVIEWID_UserChooseView`|Kullanıcıdan hangi görünümün kullanılacağını seçmesini ister.|
|`LOGVIEWID_ProjectSpecificEditor`|**Birlikte Aç** iletişim kutusu tarafından gönderildi<br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.OpenItem%2A><br /><br /> Kullanıcı "(proje varsayılan düzenleyici)" girişini seçtiğinde.|

 Mantıksal Görünüm GUID 'Leri Genişletilebilir olsa da, yalnızca VSPackage içinde tanımlanan mantıksal görünüm GUID 'Lerini kullanabilirsiniz.

 Kapatılırken, Visual Studio, düzenleyici fabrikası ve belge penceresiyle ilişkili fiziksel görünüm dizelerini, çözüm yeniden açıldığında Belge pencerelerini yeniden açmak için kullanılabilecek şekilde korur. Çözüm (. suo) dosyasında yalnızca bir çözüm kapatıldığında açık olan pencereler kalıcı hale getirilir. Bu değerler, <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> yöntemindeki `propid` parametresine geçirilen `VSFPROPID_guidEditorType` ve `VSFPROPID_pszPhysicalView` değerlere karşılık gelir.

## <a name="example"></a>Örnek
 Bu kod parçacığı, `IVsCodeWindow`uygulayan bir görünüme erişmek için <xref:Microsoft.VisualStudio.Shell.Interop.LogicalViewID.TextView> nesnesinin nasıl kullanıldığını gösterir. Bu durumda <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShellOpenDocument> hizmeti, bir pencere çerçevesine bir işaretçi alan `LOGVIEWID_TextView`<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenDocumentViaProject%2A> ve istek çağırmak için kullanılır. Belge görünümü nesnesine yönelik bir işaretçi, <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> çağırarak ve bir `VSFPROPID_DocView`değeri belirtilerek elde edilir. Belge görünümü nesnesinden, `IVsCodeWindow`için `QueryInterface` çağırılır. Bu durumda beklenmek bir metin düzenleyicisinin döndürüldüğünden, bu nedenle <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> yönteminde döndürülen belge görünümü nesnesi bir kod penceresidir.

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