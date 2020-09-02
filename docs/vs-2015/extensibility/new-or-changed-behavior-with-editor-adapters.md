---
title: Düzenleyici bağdaştırıcılarla yeni veya değiştirilmiş davranış | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - adapter behavior
ms.assetid: 5555b116-cfdb-4773-ba62-af80fda64abd
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: fc7ddaf7ec67a1e33248d5ce424868849200d3e6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68194173"
---
# <a name="new-or-changed-behavior-with-editor-adapters"></a>Düzenleyici Bağdaştırıcılarıyla Yeni veya Değiştirilmiş Davranış
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio temel düzenleyicisinin önceki sürümlerine karşı yazılmış kodu güncelleştiriyorsanız ve yeni API 'yi kullanmak yerine düzenleyici bağdaştırıcılarını (veya dolgu) kullanmayı planlıyorsanız, önceki çekirdek düzenleyiciye göre düzenleyici bağdaştırıcılarının davranışındaki aşağıdaki farklılıklara dikkat etmeniz gerekir.  
  
## <a name="features"></a>Özellikler  
  
#### <a name="using-setsite"></a>SetSite () kullanma  
 <xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite.SetSite%2A>Üzerinde başka herhangi bir işlem gerçekleştirmeden önce metin arabellekleri, metin görünümleri ve kod pencerelerini birlikte oluşturduğunuzda çağırmanız gerekir. Ancak, bu <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService> hizmetin Create () yöntemlerinin kendisi çağrı yaptığından, bunları oluşturmak için kullanırsanız, bu gerekli değildir <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.SetSite%2A> .  
  
#### <a name="hosting-ivscodewindow-and-ivstextview-in-your-own-content"></a>Kendi içeriklerinizi IVsCodeWindow ve IVsTextView barındırma  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> Win32 modunu veya WPF modunu kullanarak her ikisini de kendi içeriklerinizi barındırabilirsiniz. Ancak, iki modda bazı farklılıklar olduğunu aklınızda bulundurmanız gerekir.  
  
##### <a name="using-win32-and-wpf-versions-of-ivscodewindow"></a>IVsCodeWindow 'un Win32 ve WPF sürümlerini kullanma  
 Düzenleyici kodu penceresi, <xref:Microsoft.VisualStudio.Shell.WindowPane> eski Win32 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> arabirimini ve yeni WPF arabirimini uygulayan öğesinden türetilir <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIElementPane> . <xref:Microsoft.VisualStudio.Shell.WindowPane.Microsoft%23VisualStudio%23Shell%23Interop%23IVsWindowPane%23CreatePaneWindow%2A>BIR hwnd tabanlı barındırma ortamı oluşturmak için yöntemini veya <xref:Microsoft.VisualStudio.Shell.WindowPane.Microsoft%23VisualStudio%23Shell%23Interop%23IVsUIElementPane%23CreateUIElementPane%2A> WPF barındırma ortamı oluşturmak için yöntemini kullanabilirsiniz. Temeldeki düzenleyici her zaman WPF kullanır, ancak bu pencere bölmesini doğrudan kendi içeriğinize katıştırıyorsanız, barındırma gereksinimlerinize uyan pencere bölmesi türünü de oluşturabilirsiniz.  
  
##### <a name="using-win32-and-wpf-versions-of-ivstextview"></a>IVsTextView 'un Win32 ve WPF sürümlerini kullanma  
 Bir <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> Win32 moduna veya WPF moduna ayarlayabilirsiniz.  
  
 Bir düzenleyici fabrikası metin görünümü oluşturduğunda, varsayılan olarak bir HWND içinde barındırılır ve <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetWindowHandle%2A> BIR HWND döndürür. Düzenleyiciyi bir WPF denetiminin içine eklemek için bu modu kullanmamalısınız.  
  
 WPF moduna bir metin görünümü ayarlamak için, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.Initialize%2A> <xref:Microsoft.VisualStudio.TextManager.Interop.TextViewInitFlags3> parametresindeki başlatma bayraklarını bir tane olarak çağırmanız ve geçirmeniz gerekir `InitView` . Öğesini <xref:System.Windows.FrameworkElement> çağırarak sağlayabilirsiniz <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIElementPane.CreateUIElementPane%2A> .  
  
 WPF modu, Win32 modundan iki şekilde farklılık gösterir. İlk olarak, metin görünümü bir WPF bağlamında barındırılabilir. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIElementPane> ' İ ' a ve çağırarak wpf bölmesine erişebilirsiniz <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIElement.GetUIObject%2A> . İkincisi, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetWindowHandle%2A> hala BIR HWND döndürür, ancak bu HWND yalnızca konumunu denetlemek ve üzerinde odağı ayarlamak için kullanılabilir. Bu HWND 'yi bir WM_PAINT iletisine yanıt vermek için kullanmanız gerekir, çünkü düzenleyicinin pencereyi nasıl boyayacağını etkilemeyecektir. Bu HWND yalnızca bağdaştırıcılar aracılığıyla yeni düzenleyici koduna geçişi kolaylaştırmak için geçerlidir. `VIF_NO_HWND_SUPPORT`Bu modda ' den itibaren döndürülen HWND 'teki sınırlamalar nedeniyle, bileşeninizin çalışması için BIR HWND olması önemle önerilir `GetWindowHandle` .  
  
#### <a name="passing-arrays-as-parameters-in-native-code"></a>Yerel kodda dizi parametreleri olarak geçirme  
 Eski Düzenleyici API 'sinde bir diziyi ve bunların sayısını içeren parametrelere sahip birçok yöntem vardır. Örnekler şunlardır:  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.AppendViewOnlyMarkerTypes%2A>  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.RemoveViewOnlyMarkerTypes%2A>  
  
 Bu yöntemleri yerel kodda arıyorsanız, tek seferde yalnızca bir öğe geçirmeniz gerekir. Birden fazla öğe geçirirseniz, birincil birlikte çalışma uygulamasındaki sorunlar nedeniyle çağrı reddedilir.  
  
 Sorun, gibi yöntemlerle daha karmaşıktır <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.SetIgnoreMarkerTypes%2A> . Bu yöntem her çağrıldığında, önceki yoksayılan işaret türleri listesini temizler, bu nedenle bu yöntemi üç farklı işaret türüyle üç kez çağırmak mümkün değildir. Tek çözüm, bu yöntemi yalnızca yönetilen kodda çağırdır.  
  
#### <a name="threading"></a>İş Parçacığı Oluşturma  
 ARABIRIM iş parçacığından her zaman arabellek bağdaştırıcısını çağırmanız gerekir. Arabellek bağdaştırıcısı yönetilen bir nesnedir. Bu, yönetilen koddan çağırmak COM sıralamasını atlayacak ve çağrınıza otomatik olarak Kullanıcı arabirimi iş parçacığına sıralanmayacak anlamına gelir.  Arabellek bağdaştırıcısını bir arka plan iş parçacığından arıyorsanız, <xref:System.Windows.Threading.Dispatcher.Invoke%2A> veya benzer bir yöntem kullanmanız gerekir.  
  
#### <a name="lockbuffer-methods"></a>LockBuffer yöntemleri  
 Tüm LockBuffer () yöntemleri kullanım dışıdır. Örnekler şunlardır:  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.LockBuffer%2A>  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream.LockBuffer%2A>  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.LockBuffer%2A>  
  
#### <a name="commit-events"></a>Olayları işleyin  
 Kayıt olayları desteklenmez. Bu olayları öneren bir yöntemi çağırmak, yöntemin hata kodu döndürmesine neden olur.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsPreliminaryTextChangeCommitEvents>  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFinalTextChangeCommitEvents>  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsUndoRedoClusterWithCommitEvents>  
  
#### <a name="texteditorevents"></a>TextEditorEvents  
 <xref:EnvDTE.TextEditorEvents>Artık COMMIT () üzerinde başlatılmıyor. Bunun yerine her metin değişikliğini tetikler.  
  
#### <a name="text-markers"></a>Metin Işaretçileri  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarker.Invalidate%2A> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarker> Nesneleri kaldırdığınızda nesneler üzerinde çağırmanız gerekir. Önceki sürümlerde yalnızca işaretleyicileri serbest bırakmanız gerekir.  
  
#### <a name="line-numbers"></a>Satır numaraları  
 Ve üzerindeki çeşitli yöntemler için <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx> satır numaraları, Visual Studio 2008 ' de olduğu gibi, ana hat ve sözcük kaydırmayı gösteren satır numaralarına değil, temel alınan arabellek satırı numaralarına karşılık gelir.  
  
 Etkilenen Yöntemler aşağıdakileri içerir (liste kapsamlı değildir):  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.CenterLines%2A>  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetCaretPos%2A>  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetLineAndColumn%2A>  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetNearestPosition%2A>  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetPointOfLineColumn%2A>  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetTextStream%2A>  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetWordExtent%2A>  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.PositionCaretForEditing%2A>  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.ReplaceTextOnLine%2A>  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.SetCaretPos%2A>  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.SetSelection%2A>  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.SetTopLine%2A>  
  
#### <a name="outlining"></a>Anahat Oluşturma  
 İstemcileri <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> yalnızca veya kullanılarak eklenen ana hat bölgelerini görür <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession.AddHiddenRegions%2A> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSessionEx.AddHiddenRegionsEx%2A> . Bunlar, düzenleyici bağdaştırıcıları üzerinden eklenmediği için geçici bölgeleri görmez. Benzer şekilde, bu istemciler, düzenleyici bağdaştırıcıları yerine yeni düzenleyici kodu kullanan diller (C# ve C++ dahil) tarafından eklenen ana hat bölgelerini görmez.  
  
#### <a name="line-heights"></a>Çizgi yükseklikleri  
 Yeni düzenleyicide, metin satırları, yazı tipi boyutuna ve satırı diğer satırlara göre taşıyabilirler olası çizgi dönüştürmelerini bağlı olarak farklı yükseklikleri içerebilir Gibi yöntemler tarafından döndürülen çizgi yüksekliği, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetLineHeight%2A> varsayılan yazı tipi boyutu uygulanmış bir satır dönüştürmesiz bir satırın yüksekliğidir. Bu yükseklik görünümdeki bir çizginin gerçek yüksekliğini gösterebilir veya yansıtmayabilir.  
  
#### <a name="eventing-and-undo"></a>Olay ve geri alma  
 Yeni düzenleyicide görünüm, geri alma kümesi açık olduğunda bile olayları sürekli olarak işleme ve oluşturma gibi işlemler gerçekleştirmeye devam eder. Bu davranış, geri alma kümesinin kapanışına kadar bu işlemleri gerçekleştirmeyen eski görünümlerden farklıdır.  
  
#### <a name="intellisense"></a>IntelliSense  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.UpdateTipWindow%2A>Ya da gerçekleştirmeyen bir sınıf geçirirseniz, yöntemi başarısız olur <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextTipWindow2> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow3> . Özel Win32 sahibi tarafından çizilen açılan pencereler artık desteklenmiyor.  
  
#### <a name="smarttags"></a>SmartTags  
 ,, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsSmartTagData> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsSmartTagTipWindow> Ve arabirimleriyle oluşturulan Akıllı etiketlere yönelik bir bağdaştırıcı desteği yoktur <xref:Microsoft.VisualStudio.TextManager.Interop.IVsSmartTagTipWindow2> .  
  
#### <a name="dte"></a>MIÞTIR  
 <xref:EnvDTE80.IncrementalSearch> uygulanmadı.  
  
## <a name="unimplemented-methods"></a>Uygulanmayan Yöntemler  
 Metin arabelleği bağdaştırıcısında, metin görünümü bağdaştırıcısında ve metin katmanı bağdaştırıcısında bazı yöntemler uygulanmadı.  
  
|Arabirim|Uygulanmadı|  
|---------------|---------------------|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>|`Reload(false)` uygulanmadı.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.EnumSpans%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.SetBufferMappingModes%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.SetSpanMappings%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.GetMarkerData%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.ReleaseMarkerData%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.CanReplaceLines%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.CopyLineText%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.CreateTrackingPoint%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.EnumLayerMarkers%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.GetBaseBuffer%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.GetLengthOfLine%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.GetLineCount%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.GetLineText%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.GetMarkerData%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.LockBufferEx%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.MapLocalSpansToTextOriginatingLayer%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.ReleaseMarkerData%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.ReplaceLines%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.ReplaceLinesEx%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.UnlockBufferEx%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Find%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Replace%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLayeredTextView>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLayeredTextView.GetSelectedAtom%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetSelectionDataObject%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.PositionCaretForEditing%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.RestrictViewRange%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateViewFrameCaption%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.GetSmartTagRect%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.InvokeInsertionUI%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.SetHoverWaitTimer%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow.SetViewClassID%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.AfterCompletorCommit%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.BeforeCompletorCommit%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.Exec%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetContextLocation%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetServiceProvider%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetSmartTagRect%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetSubjectCaretPos%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetSubjectSelection%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetSubjectText%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.QueryStatus%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.ReplaceSubjectTextSpan%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.SetSubjectCaretPos%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.SetSubjectSelection%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.UpdateSmartTagWindow%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewIntellisenseHost>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewIntellisenseHost.SetSubjectFromPrimaryBuffer%2A> , bağdaştırıcılara uygulanır ancak ana hat Kullanıcı arabirimi tarafından yok sayılır.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenRegionEx>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenRegionEx.GetBannerAttr%2A> , bağdaştırıcılara uygulanır ancak ana hat Kullanıcı arabirimi tarafından yok sayılır.|
