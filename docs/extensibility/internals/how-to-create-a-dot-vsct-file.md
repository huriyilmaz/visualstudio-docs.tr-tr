---
title: 'Nasıl: Oluşturma. Vsct Dosya | Microsoft Docs'
description: XML tabanlı bir dosya olan .vsct dosyasını el ile Visual Studio tablo yapılandırma dosyasını öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- VSCT files, creating
ms.assetid: b955f51c-f9f9-49c3-a8e4-63b6eb0e0341
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: fa80c77a9ed390e55e39b72c0ea5976f0584b25b
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122063336"
---
# <a name="how-to-create-a-vsct-file"></a>Nasıl: .vsct dosyası oluşturma

XML tabanlı bir komut tablosu yapılandırması (*.vsct*) Visual Studio oluşturmak için çeşitli yollar vardır.

- Paket şablonunda yeni bir VSPackage [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] oluşturabilirsiniz.

- Var olan bir .ctc dosyasından dosya oluşturmak için *Vsct.exe* XML tabanlı komut tablosu yapılandırma *derleyicisini kullanabilirsiniz.*

- Var olan *bir .cto* dosyasından *.vsct* dosyası oluşturmak içinVsct.exe'yi *kullanabilirsiniz.*

- El ile yeni bir *.vsct dosyası oluşturabilirsiniz.*

  Bu makalede el ile yeni bir *.vsct* dosyası oluşturma açıklanmıştır.

### <a name="to-manually-create-a-new-vsct-file"></a>El ile yeni bir .vsct dosyası oluşturmak için

1. 'i [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] başlatma.

2. Dosya menüsünde **Yeni'nin** üzerine **gelin ve** Ardından Dosya'ya **tıklayın.**

3. Şablonlar bölmesinde **XML Dosyası'nın** ardından **Aç'a** **tıklayın.**

4. Görünüm **menüsünde,** XML **dosyasının özelliklerini** görüntülemek için Özellikler'e tıklayın.

5. Özellikler **penceresinde** Şemalar **özelliğinde** Gözat **düğmesine** tıklayın.

6. XSD şemaları listesinde *vsct.xsd şemasını* seçin. Listede yoksa Ekle'ye **tıklayın** ve ardından dosyayı yerel sürücüde bulun. Bitirdikten **sonra** Tamam'a tıklayın.

7. XML *dosyasında, CommandTable'<ve ardından* Tab tuşuna **basın.** yazarak etiketi *>* kapatın.

    Bu eylem temel bir *.vsct dosyası* oluşturur.

8. VSCT XML şema başvurusuna göre eklemek istediğiniz XML dosyasının [öğelerini doldurun.](../../extensibility/vsct-xml-schema-reference.md) Daha fazla bilgi için [bkz. Author .vsct files](../../extensibility/internals/authoring-dot-vsct-files.md).

<a name="how-to-create-a-dot-vsct-file-from-an-existing-dot-ctc-file"></a>

## <a name="how-to-create-a-vsct-file-from-an-existing-ctc-file"></a>Nasıl olur: Mevcut bir .ctc dosyasından .vsct Dosyası oluşturma

Var olan bir komut tablosu *.ctc kaynak* dosyasından XML tabanlı *.vsct dosyası* oluşturabilirsiniz. Bunu yaparak, yeni XML tabanlı komut tablosu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] (VSCT) derleyici biçiminden faydalanabilirsiniz.

### <a name="to-create-a-vsct-file-from-a-ctc-file"></a>Bir .ctc dosyasından .vsct dosyası oluşturmak için

1. Perl dilinin bir kopyasını alın.

2. Genellikle *\<Visual Studio SDK installation path> \VisualStudioIntegration\Tools\bin* klasöründe bulunan Perl betiği ConvertCTCToVSCT.pl kopyasını alın. 

3. Dönüştürmek istediğiniz *.ctc kaynak* dosyasının bir kopyasını alın.

4. Dosyaları aynı dizine yer.

5. Komut [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] istemi penceresinde dizinine gidin.

6. Tür

   ```
   perl.exe ConvertCTCtoVSCT.pl PkgCmd.ctc PkgCmd.vsct
   ```

    Burada *PkgCmd.ctc,* *.ctc* dosyasının adı, *PkgCmd.vsct* ise oluşturmak istediğiniz *.vsct* dosyasının adıdır.

    Bu eylem yeni bir *.vsct* XML komut tablosu kaynak dosyası oluşturur. Dosyayı, vsCT *derleyicisiVsct.exe* herhangi bir *.vsct* dosyası gibi kullanarak derleyebilirsiniz.

   > [!NOTE]
   > XML açıklamalarını yeniden adlandırarak *.vsct* dosyasının okunabilirliğini geliştirebilirsiniz.

<a name="how-to-create-a-dot-vsct-file-from-an-existing-dot-cto-file"></a>

## <a name="how-to-create-a-vsct-file-from-an-existing-cto-file"></a>Nasıl olur: Mevcut bir .cto dosyasından .vsct dosyası oluşturma

Var olan bir ikili *.cto* dosyasından XML tabanlı *.vsct* dosyası oluşturabilirsiniz. Bunu yapmak, yeni komut tablosu derleyici biçiminden yararlanmaya olanak sağlar. Bu işlem, *.cto dosyası bir .ctc* dosyasından derlenmiş *olsa bile* çalışır. *.vsct* dosyasını düzenleyemez ve başka bir .cto dosyasına derleyebilirsiniz.

### <a name="to-create-a-vsct-file-from-a-cto-file"></a>Bir .cto dosyasından .vsct dosyası oluşturmak için

1. *.cto* dosyasının ve karşılık gelen *.ctsym dosyasının kopyalarını* alın.

2. Dosyaları veri derleyicisi ile aynı *dizinevsct.exe.*

3. Komut *Visual Studio.cto* ve *.ctsym* dosyalarını içeren dizine gidin.

4. Tür

    ```
    vsct.exe <ctofilename>.cto <vsctfilename>.vsct -S<symfilename>.ctsym
    ```

     burada , .cto dosyasının adıdır, oluşturmak istediğiniz .vsct dosyasının adıdır ve \<ctofilename\>  \<vsctfilename\>  \<symfilename\> *.ctsym* dosyasının adıdır.

     Bu işlem yeni bir *.vsct* XML komut tablosu derleyici dosyası oluşturur. Diğer *.vsct* dosyalarında *olduğuvsct.exe* vsct derleyicisi ile dosyayı düzenleyebilir ve derebilirsiniz.

## <a name="compile-the-code"></a>Kodu derleme
 Bir projeye *.vsct* dosyası eklemek derlemeye neden olmaz. Bunu derleme sürecine dahil etmek gerekir.

### <a name="to-add-a-vsct-file-to-project-compilation"></a>Proje derlemeye bir .vsct dosyası eklemek için

1. Proje dosyanızı düzenleyicide açın. Proje yüklü ise, önce projenin yüklemesini kaldırmalısiniz.

2. Aşağıdaki örnekte gösterildiği gibi bir öğesi içeren bir [ItemGroup](../../msbuild/itemgroup-element-msbuild.md) `VSCTCompile` öğesi ekleyin.

    ```xml
    <ItemGroup>
      <VSCTCompile Include="TopLevelMenu.vsct">
        <ResourceName>Menus.ctmenu</ResourceName>
      </VSCTCompile>
    </ItemGroup>

    ```

     öğesinin `ResourceName` her zaman olarak ayarlanmış olması `Menus.ctmenu` gerekir.

3. Projeniz bir *.resx* dosyası içeriyorsa, aşağıdaki örnekte gösterildiği gibi bir öğesi `EmbeddedResource` içeren bir öğe `MergeWithCTO` ekleyin:

    ```xml
    <EmbeddedResource Include="VSPackage.resx">
      <MergeWithCTO>true</MergeWithCTO>
      <ManifestResourceName>VSPackage</ManifestResourceName>
    </EmbeddedResource>

    ```

     Bu işaretleme, eklenmiş kaynakları `ItemGroup` içeren öğenin içine girilir.

4. Düzenleyicide genellikle *\<ProjectName\> Package.cs veya* *\<ProjectName\> Package.vb adlı paket* dosyasını açın.

5. Aşağıdaki `ProvideMenuResource` örnekte gösterildiği gibi paket sınıfına bir öznitelik ekleyin.

    ```csharp
    [ProvideMenuResource("Menus.ctmenu", 1)]
    ```

     İlk parametre değeri, proje dosyasında `ResourceName` tanımlandığı özniteliğin değeriyle eşleşmeli.

## <a name="see-also"></a>Ayrıca bkz.
- [.vsct dosyaları yazma](../../extensibility/internals/authoring-dot-vsct-files.md)
- [Visual Studio tablosu (.vsct) dosyaları](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [VSCT XML şema başvurusu](../../extensibility/vsct-xml-schema-reference.md)
