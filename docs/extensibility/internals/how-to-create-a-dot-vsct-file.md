---
title: 'Nasıl yapılsın: Bir . Vsct Dosyası | Microsoft Dokümanlar'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, creating
ms.assetid: b955f51c-f9f9-49c3-a8e4-63b6eb0e0341
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a5a5f53ec87c9447af232e9d0528108ddbaea01a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708116"
---
# <a name="how-to-create-a-vsct-file"></a>Nasıl yapılsın: .vsct dosyası oluşturma

XML tabanlı Visual Studio komut tablosu yapılandırması (*.vsct*) dosyası oluşturmanın birkaç yolu vardır.

- Paket şablonunda [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] yeni bir VSPackage oluşturabilirsiniz.

- Varolan bir *.ctc* dosyasından dosya oluşturmak için XML tabanlı komut tablosu yapılandırma derleyicisi, *Vsct.exe'yi*kullanabilirsiniz.

- Varolan bir *.cto* dosyasından *.vsct* dosyası oluşturmak için *Vsct.exe'yi* kullanabilirsiniz.

- Yeni bir *.vsct* dosyası el ile oluşturabilirsiniz.

  Bu makalede, yeni bir *.vsct* dosyasının el ile nasıl oluşturulutamamolduğu açıklanmaktadır.

### <a name="to-manually-create-a-new-vsct-file"></a>Yeni bir .vsct dosyası oluşturmak için

1. Başlat. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]

2. **Dosya** menüsünde **Yeni'yi**işaret edin ve ardından **Dosya'yı**tıklatın.

3. **Şablonlar** bölmesinde **XML Dosyası'nı** tıklatın ve sonra **Aç'ı**tıklatın.

4. **Görünüm** menüsünde, XML dosyasının özelliklerini görüntülemek için **Özellikler'i** tıklatın.

5. **Özellikler** penceresinde, **Şems** özelliğindeki **Gözat** düğmesini tıklatın.

6. XSD şemaları listesinde *vsct.xsd* şema sını seçin. Listede yoksa, **Ekle'yi** tıklatın ve ardından yerel bir sürücüde dosyayı bulun. Bittiğinde **Tamam'ı** tıklatın.

7. XML dosyasında, *CommandTable<* yazın ve ardından **Sekme**tuşuna basın. Yazarak *>* etiketi kapatın.

    Bu eylem temel bir *.vsct* dosyası oluşturur.

8. [VSCT XML şeması referansına](../../extensibility/vsct-xml-schema-reference.md)göre eklemek istediğiniz XML dosyasının öğelerini doldurun. Daha fazla bilgi için [Author .vsct dosyalarına](../../extensibility/internals/authoring-dot-vsct-files.md)bakın.

<a name="how-to-create-a-dot-vsct-file-from-an-existing-dot-ctc-file"></a>

## <a name="how-to-create-a-vsct-file-from-an-existing-ctc-file"></a>Nasıl yapilir: Varolan bir .ctc dosyasından .vsct Dosyası oluşturma

Varolan bir komut tablosu *.ctc* kaynak dosyasından XML tabanlı *.vsct* dosyası oluşturabilirsiniz. Bunu yaparak, yeni XML tabanlı [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] komut tablosu (VSCT) derleyici biçiminden yararlanabilirsiniz.

### <a name="to-create-a-vsct-file-from-a-ctc-file"></a>.ctc dosyasından .vsct dosyası oluşturmak için

1. Perl dilinin bir kopyasını alın.

2. Genellikle * \<Visual Studio SDK yükleme yolu>\VisualStudioIntegration\Tools\bin* klasöründe bulunan Perl komut dosyası *ConvertCTCToVSCT.pl nın*bir kopyasını edinin.

3. Dönüştürmek istediğiniz *.ctc* kaynak dosyasının bir kopyasını edinin.

4. Dosyaları aynı dizine yerleştirin.

5. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Komut istemi penceresinde, dizine gidin.

6. Tür

   ```
   perl.exe ConvertCTCtoVSCT.pl PkgCmd.ctc PkgCmd.vsct
   ```

    *PkgCmd.ctc.ctc.ctc.ctc* dosyasının adı dır ve *PkgCmd.vsct* oluşturmak istediğiniz *.vsct* dosyasının adıdır. *.ctc*

    Bu eylem yeni bir *.vsct* XML komut tablosu kaynak dosyası oluşturur. Dosyayı *vsct.exe*, VSCT derleyicisi, diğer *.vsct* dosyagibi kullanarak dosyayı derleyebilirsiniz.

   > [!NOTE]
   > XML yorumlarını yeniden biçimlendirmek için *.vsct* dosyasının okunabilirliğini artırabilirsiniz.

<a name="how-to-create-a-dot-vsct-file-from-an-existing-dot-cto-file"></a>

## <a name="how-to-create-a-vsct-file-from-an-existing-cto-file"></a>Nasıl yapilir: Varolan bir .cto dosyasından .vsct dosyası oluşturma

Varolan bir ikili *.cto* dosyasından XML tabanlı *.vsct* dosyası oluşturabilirsiniz. Bunu yapmak, yeni komut tablosu derleyici biçiminden yararlanmanızı sağlar. *.cto* dosyası bir *.ctc* dosyasından derlenmiş olsa bile bu işlem çalışır. *.vsct* dosyasını başka bir .cto dosyasında disep derleyebilirsiniz.

### <a name="to-create-a-vsct-file-from-a-cto-file"></a>.cto dosyasından .vsct dosyası oluşturmak için

1. *.cto* dosyasının ve ilgili *.ctsym* dosyasının kopyalarını alın.

2. Dosyaları *vsct.exe* derleyicisi ile aynı dizine yerleştirin.

3. Visual Studio komut isteminde *.cto* ve *.ctsym* dosyalarını içeren dizine gidin.

4. Tür

    ```
    vsct.exe <ctofilename>.cto <vsctfilename>.vsct -S<symfilename>.ctsym
    ```

     ctofilename \<\> *.cto* dosyasının adı, \<vsctfilename\> oluşturmak istediğiniz *.vsct* dosyasının adı dır \<ve\> symfilename *.ctsym* dosyasının adıdır.

     Bu işlem yeni bir *.vsct* XML komut tablosu derleyici soluşturur. Dosyayı *vsct.exe*, vsct derleyicisi, diğer *.vsct* dosyası gibi birlikte diseve derleyebilirsiniz.

## <a name="compile-the-code"></a>Kodu derleme
 Bir projeye *bir .vsct* dosyası eklemek, dosyanın derlenmesine neden olmaz. Yapı işlemine dahil etmelisiniz.

### <a name="to-add-a-vsct-file-to-project-compilation"></a>Proje derlemesine .vsct dosyası eklemek için

1. Proje dosyanızı düzenleyicide açın. Proje yüklenmişse, önce boşaltmanız gerekir.

2. Aşağıdaki örnekte gösterildiği gibi, bir öğe içeren bir `VSCTCompile` [ItemGroup öğesi](../../msbuild/itemgroup-element-msbuild.md) ekleyin.

    ```xml
    <ItemGroup>
      <VSCTCompile Include="TopLevelMenu.vsct">
        <ResourceName>Menus.ctmenu</ResourceName>
      </VSCTCompile>
    </ItemGroup>

    ```

     Öğe `ResourceName` her zaman ' `Menus.ctmenu`olarak ayarlanmalıdır.

3. Projeniz bir *.resx* dosyası içeriyorsa, `MergeWithCTO` aşağıdaki örnekte gösterildiği gibi bir öğe içeren bir `EmbeddedResource` öğe ekleyin:

    ```xml
    <EmbeddedResource Include="VSPackage.resx">
      <MergeWithCTO>true</MergeWithCTO>
      <ManifestResourceName>VSPackage</ManifestResourceName>
    </EmbeddedResource>

    ```

     Bu biçimlendirme, katışılmış kaynaklar içeren öğenin `ItemGroup` içine girmelidir.

4. Genellikle * \<ProjectName Package.cs\>* veya * \<ProjectName\>Package.vb*adlı paket dosyasını düzenleyicide açın.

5. Aşağıdaki `ProvideMenuResource` örnekte gösterildiği gibi paket sınıfına bir öznitelik ekleyin.

    ```csharp
    [ProvideMenuResource("Menus.ctmenu", 1)]
    ```

     İlk parametre değeri, proje dosyasında tanımladığınız özniteliğin `ResourceName` değeriyle eşleşmelidir.

## <a name="see-also"></a>Ayrıca bkz.
- [Yazar .vsct dosyaları](../../extensibility/internals/authoring-dot-vsct-files.md)
- [Visual Studio komut tablosu (.vsct) dosyaları](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [VSCT XML şema referansı](../../extensibility/vsct-xml-schema-reference.md)
