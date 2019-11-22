---
title: Kodlanmış UI Testleriyle SharePoint 2010 uygulamalarını test etme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: 51b53778-469c-4cc9-854c-4e4992d6389b
caps.latest.revision: 32
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 73dd0e406e8e0a00260d922e38dee70135c3645d
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74298011"
---
# <a name="testing-sharepoint-2010-applications-with-coded-ui-tests"></a>Kodlanmış UI Testleriyle SharePoint 2010 Uygulamalarını Test Etme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kodlanmış UI testlerini bir SharePoint uygulamasına dahil etmek, Kullanıcı arabirimi denetimleri de dahil olmak üzere tüm uygulamanın düzgün çalıştığını doğrulamanızı sağlar. Kodlanmış UI testleri, Kullanıcı arabirimindeki değerleri ve mantığı da doğrulayabilir.

 **Gereksinimler**

- Visual Studio Enterprise

## <a name="what-else-should-i-know-about-coded-ui-tests"></a>Kodlanmış UI testleri hakkında başka ne bilmeliyim?
 Kodlanmış UI testlerini kullanmanın avantajları hakkında daha fazla bilgi edinmek için bkz. [Visual Studio 2012 – Bölüm 5 ' i kullanarak sürekli teslim Için](https://go.microsoft.com/fwlink/?LinkID=255196) [kodunuzu test etmek Için UI Otomasyonunu kullanma](../test/use-ui-automation-to-test-your-code.md) .

 **Notlar**

- ![Prerequsite](../test/media/prereq.png "Önkoşul") SharePoint uygulamaları için kodlanmış UI testleri yalnızca SharePoint 2010 ile desteklenir.

- ![Prerequsite](../test/media/prereq.png "Önkoşul") SharePoint uygulamanızda Visio ve PowerPoint 2010 denetimleri için destek desteklenmez.

## <a name="creating-a-coded-ui-test-for-your-sharepoint-app"></a>SharePoint uygulamanız için kodlanmış UI testi oluşturma
 SharePoint 2010 uygulamalarınız için [KODLANMıŞ UI testleri oluşturmak](../test/use-ui-automation-to-test-your-code.md#VerifyingCodeUsingCUITCreate) , diğer uygulama türleri için test oluşturma ile aynıdır. Kayıt ve kayıttan yürütme, Web düzenlemesi arabirimindeki tüm denetimler için desteklenir. Kategorileri ve Web parçalarını seçme arabirimi tüm standart Web denetimleridir.

 ![SharePoint Web bölümleri](../test/media/cuit-sharepoint.png "CUIT_SharePoint")

> [!NOTE]
> Eylem kaydediyorsanız, kodu oluşturmadan önce eylemleri doğrulayın. Fare vurgusu ile ilişkili birkaç davranış olduğundan, varsayılan olarak açık olur. Kodlanmış UI testlerinizden gereksiz bir yere dikkat kaldırmayı dikkatli olun. Bunu, test için kodu düzenleyerek veya [KODLANMıŞ UI test düzenleyicisini](../test/editing-coded-ui-tests-using-the-coded-ui-test-editor.md)kullanarak yapabilirsiniz.

## <a name="including-testing-of-office-2010-controls-within-your-sharepoint-app"></a>SharePoint uygulamanızda Office 2010 denetimlerinin test edilmesi dahil
 SharePoint uygulamanızda bazı Office 2010 Web bölümleri için Otomasyonu etkinleştirmek üzere bazı küçük kod değişiklikleri yapmanız gerekir.

> [!WARNING]
> Visio ve PowerPoint 2010 denetimleri için destek desteklenmez.

### <a name="excel-2010-cell-controls"></a>Excel 2010 hücre denetimleri
 Excel hücre denetimlerini dahil etmek için, kodlanmış UI testinin kodunda bazı değişiklikler yapmanız gerekir.

> [!WARNING]
> Herhangi bir Excel hücresine metin girme, ardından bir ok tuşu eyleminden, doğru şekilde kayıt yapmaz. Hücreleri seçmek için fareyi kullanın.

 Eylemleri boş bir hücreye kaydediyorsanız, hücreyi çift tıklayarak ve ardından bir metin ayarla işlemi gerçekleştirerek kodu değiştirmeniz gerekir. Bu, hücreye tıkladığınızda ve ardından herhangi bir klavye eyleminin ardından hücre içinde `textarea` etkinleştirmediği için gereklidir. Boş hücrede `setvalue` kaydetmek, hücreye tıklanana kadar mevcut olmayan `editbox` arar. Örneğin:

```csharp
Mouse.DoubliClick(uiItemCell,new Point(31,14));
uiGridKeyboardInputEdit.Text=value;
```

 Boş olmayan bir hücrede eylem kaydediyorsanız, bir hücreye metin eklediğiniz anda yeni bir \<div > denetimi hücrenin bir alt öğesi olarak eklenir, daha sonra kaydetme işlemi biraz daha karmaşıktır. Yeni \<div > denetimi, az önce girdiğiniz metni içerir. Kaydedicinin, yeni \<div > denetimine eylemleri kaydetmesi gerekir; Ancak, test girilene kadar yeni \<div > denetimi mevcut olmadığından, bu yapılamıyor. Bu sorunu karşılamak için aşağıdaki kod değişikliklerini el ile yapmanız gerekir.

1. Hücre başlatmaya gidin ve `RowIndex` ve `ColumnIndex` birincil özellikleri yapın:

    ```csharp
    this.mUIItemCell.SearchProperties[HtmlCell.PropertyNames. RowIndex] = "3";
    this.mUIItemCell.SearchProperties[HtmlCell.PropertyNames. ColumnIndex] = "3";
    ```

2. Hücrenin `HtmlDiv` çocuğu bulun:

    ```csharp
    private UITestControl getControlToDoubleClick(HtmlCell cell)
    {
         if (String.IsNullOrEmpty(cell.InnerText)) return cell;
         HtmlDiv pane = new HtmlDiv(cell);
         pane.FilterProperties[HtmlDiv.PropertyNames.InnerText] = cell.InnerText;
         // Class is an important property in finding pane
         pane.FilterProperties[HtmlDiv.PropertyNames.Class] = "cv-nwr";
         UITestControlCollection panes = pane.FindMatchingControls();
         return panes[0];
    }

    ```

3. `HtmlDiv`üzerinde fare çift tıklama eylemi için kod ekleyin:

    ```csharp
    Mouse.DoubleClick(uIItemPane, new Point(31, 14)); )
    ```

4. `TextArea`metin ayarlamak için kod ekleyin:

    ```csharp
    uIGridKeyboardInputEdit.Text = value; }
    ```

## <a name="enabling-coded-ui-testing-of-silverlight-web-parts-in-your-sharepoint-2010-app"></a>SharePoint 2010 uygulamanızda Silverlight Web bölümlerinin kodlanmış UI testlerini etkinleştirme
 Silverlight testi Visual Studio 2012 ve üzeri sürümlerde desteklenmez. Ancak, Silverlight Web bölümlerini SharePoint 2010 uygulamanızda test etmek istiyorsanız, Visual Studio galerisinden ayrı bir Silverlight eklentisi yükleyebilirsiniz.

#### <a name="setting-up-your-machine"></a>Makinenizi ayarlama

1. Visual Studio 2012,1 veya sonraki bir sürümünün yüklü olduğundan emin olun.

2. [Silverlight için MICROSOFT VISUAL STUDIO UI test eklentisi](https://marketplace.visualstudio.com/items?itemName=PrachiBoraMSFT.MicrosoftVisualStudioUITestPluginforSilverlight)' ni yükler.

3. [Fiddler](http://www.fiddler2.com/fiddler2/)'i yükler. Bu, yalnızca HTTP trafiğini yakalayan ve günlüğe kaydeden bir araçtır.

4. [FiddlerXap projesini](https://40jajy3iyl373v772m19fybm-wpengine.netdna-ssl.com/wp-content/uploads/sites/6/2019/02/FiddlerXapProxy.zip)indirin. Dosya sıkıştırmasını açın, oluşturun ve "CopySLHelper. bat" betiğini çalıştırarak, Fiddler aracını kullanırken Silverlight Web bölümlerini test etmek için gerekli olan yardımcı DLL 'yi çalıştırın.

   Makinenizi ayarladıktan sonra, SharePoint 2010 uygulamanızı Silverlight Web parçalarıyla teste başlamak için şu adımları izleyin:

#### <a name="testing-silverlight-web-parts"></a>Silverlight Web parçalarını test etme

1. Fiddler 'ı başlatın.

2. Tarayıcı önbelleğini temizleyin. Bu gereklidir çünkü Silverlight UI Otomasyon Yardımcısı DLL 'sini içeren XAP dosyası tipik olarak önbelleğe alınır. Değiştirilen XAP dosyasının çekildiğinizden emin olmak istiyoruz, bu nedenle tarayıcı önbelleğini temizliyoruz.

3. Web sayfasını açın.

4. Kaydediciyi başlatın ve normal bir Web uygulaması testi için yaptığınız gibi kod oluşturun.

5. Oluşturulan kodun Microsoft. VisualStudio. TestTools. UITest. Extension. Silverlight. dll dosyasına başvurduğundan emin olmanız gerekir.

     Daha fazla bilgi için bkz. [Visual Studio 2012 Ile SharePoint 2010 Için UI test etme](https://devblogs.microsoft.com/devops/ui-testing-sharepoint-2010-with-visual-studio-2012/)

## <a name="external-resources"></a>Dış kaynaklar

### <a name="blogs"></a>Bloglar
 [Visual Studio 2012 ile SharePoint 2010 için Kullanıcı arabirimi test etme](https://devblogs.microsoft.com/devops/ui-testing-sharepoint-2010-with-visual-studio-2012/)

 [Kodlanmış UI testinde Silverlight denetimleri için arama mantığını anlama](https://tapas-techsnips.blogspot.com/)

 [Silverlight denetiminin özelliği getiriliyor](https://tapas-techsnips.blogspot.com/)

 [Kodlanmış UI testi için içerik dizini](https://blogs.msdn.microsoft.com/mathew_aniyan/2013/02/18/content-index-for-coded-ui-test/)

### <a name="guidance"></a>Rehber
 [Visual Studio 2012 ile sürekli teslim için test etme – Bölüm 5 Sistem testlerini otomatikleştirme](https://go.microsoft.com/fwlink/?LinkID=255196)

### <a name="forum"></a>Forum
 [Visual Studio ALM + Team Foundation Server blogu](https://go.microsoft.com/fwlink/?LinkID=254496)

## <a name="see-also"></a>Ayrıca Bkz.
 Kod [Web performansınızı test etmek ve sharepoint 2010 ve 2013 uygulamalarında yük](https://msdn.microsoft.com/library/20c2e469-0e4e-4296-a739-c0e8fff36e54) testi [yapmak Için UI Otomasyonu kullanma](../test/use-ui-automation-to-test-your-code.md) SharePoint [çözümlerini oluşturma](https://msdn.microsoft.com/library/4bfb1e59-97c9-4594-93f8-3068b4eb9631) [ve hata ayıklama](https://msdn.microsoft.com/library/b5f3bce2-6a51-41b1-a292-9e384bae420c) SharePoint [çözümlerini derleme ve hata ayıklama](https://msdn.microsoft.com/library/c9e7c9ab-4eb3-40cd-a9b9-6c2a896f70ae) SharePoint [uygulamalarının performansı profili](https://msdn.microsoft.com/library/61ae02e7-3f37-4230-bae1-54a498c2fae8) oluşturma
