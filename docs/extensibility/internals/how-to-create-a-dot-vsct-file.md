---
title: 'Nasıl yapılır: oluşturma. Vsct dosyası | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- VSCT files, creating
ms.assetid: b955f51c-f9f9-49c3-a8e4-63b6eb0e0341
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a571098deeeca0e8262d855c24d0bf1ce66be08e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85905533"
---
# <a name="how-to-create-a-vsct-file"></a>Nasıl yapılır:. vsct dosyası oluşturma

XML tabanlı Visual Studio komut tablosu yapılandırma (*. vsct*) dosyası oluşturmanın birkaç yolu vardır.

- Paket şablonunda yeni bir VSPackage oluşturabilirsiniz [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

- Var olan bir *. CTC* dosyasından bir dosya oluşturmak IÇIN, XML tabanlı komut tablosu yapılandırma derleyicisini *Vsct.exe*kullanabilirsiniz.

- Var olan bir *. CTO* dosyasından bir *. vsct* dosyası oluşturmak için *Vsct.exe* kullanabilirsiniz.

- El ile yeni bir *. vsct* dosyası oluşturabilirsiniz.

  Bu makalede, el ile yeni bir *. vsct* dosyası oluşturma açıklanır.

### <a name="to-manually-create-a-new-vsct-file"></a>El ile yeni bir. vsct dosyası oluşturmak için

1. Başlatın [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

2. **Dosya** menüsünde, **Yeni**' nin üzerine gelin ve ardından **Dosya**' ya tıklayın.

3. **Şablonlar** bölmesinde, **XML dosyası** ' na ve sonra **Aç**' a tıklayın.

4. **Görünüm** menüsünde **Özellikler** ' e tıklayarak XML dosyasının özelliklerini görüntüleyin.

5. **Özellikler** penceresinde, **şemalar** özelliğindeki **Gözden** geçirme düğmesine tıklayın.

6. XSD şemaları listesinde *vsct. xsd* şemasını seçin. Listede yoksa, **Ekle** ' ye tıklayın ve dosyayı yerel bir sürücüde bulun. İşiniz bittiğinde **Tamam** ' a tıklayın.

7. XML dosyasında *<CommandTable* yazın ve ardından **Tab**tuşuna basın. Yazarak etiketi kapatın *>* .

    Bu eylem, temel bir *. vsct* dosyası oluşturur.

8. [VSCT XML şema başvurusuna](../../extensibility/vsct-xml-schema-reference.md)göre eklemek istediğiniz XML dosyasının öğelerini girin. Daha fazla bilgi için bkz. [Author. vsct dosyaları](../../extensibility/internals/authoring-dot-vsct-files.md).

<a name="how-to-create-a-dot-vsct-file-from-an-existing-dot-ctc-file"></a>

## <a name="how-to-create-a-vsct-file-from-an-existing-ctc-file"></a>Nasıl yapılır: var olan bir. CTC dosyasından. vsct dosyası oluşturma

Varolan bir komut tablosu *. CTC* kaynak dosyasından XML tabanlı *. vsct* dosyası oluşturabilirsiniz. Bunu yaparak, yeni XML tabanlı [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] komut tablosu (VSCT) derleyici biçiminden yararlanabilirsiniz.

### <a name="to-create-a-vsct-file-from-a-ctc-file"></a>. CTC dosyasından bir. vsct dosyası oluşturmak için

1. Perl dilinin bir kopyasını alın.

2. Genellikle * \<Visual Studio SDK installation path> \VisualStudioIntegration\Tools\bin* klasöründe bulunan Perl betiğinin *ConvertCTCToVSCT.pl*bir kopyasını alın.

3. Dönüştürmek istediğiniz *. CTC* kaynak dosyasının bir kopyasını alın.

4. Dosyaları aynı dizine yerleştirin.

5. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Komut istemi penceresinde, dizinine gidin.

6. Tür

   ```
   perl.exe ConvertCTCtoVSCT.pl PkgCmd.ctc PkgCmd.vsct
   ```

    Burada *PkgCmd. CTC* , *. CTC* dosyasının adı ve *PkgCmd. vsct* , oluşturmak istediğiniz *. vsct* dosyasının adıdır.

    Bu eylem yeni bir *. vsct* XML komut tablosu kaynak dosyası oluşturur. Dosyayı, başka bir *. vsct* dosyası gibi *Vsct.exe*, vsct derleyicisini kullanarak derleyebilirsiniz.

   > [!NOTE]
   > XML açıklamalarını yeniden düzenleyerek *. vsct* dosyasının okunabilirliğini geliştirebilirsiniz.

<a name="how-to-create-a-dot-vsct-file-from-an-existing-dot-cto-file"></a>

## <a name="how-to-create-a-vsct-file-from-an-existing-cto-file"></a>Nasıl yapılır: var olan bir. CTO dosyasından. vsct dosyası oluşturma

Var olan bir binary *. CTO* dosyasından XML tabanlı *. vsct* dosyası oluşturabilirsiniz. Bunun yapılması, yeni komut tablosu derleyici biçiminden yararlanmanızı sağlar. *. CTO* dosyası bir *. CTC* dosyasından derlense bile bu işlem işe yarar. *. Vsct* dosyasını başka bir. cto dosyasına düzenleyebilir ve derleyebilirsiniz.

### <a name="to-create-a-vsct-file-from-a-cto-file"></a>. CTO dosyasından bir. vsct dosyası oluşturmak için

1. *. CTO* dosyasının ve karşılık gelen *. ctsyma* dosyasının kopyalarını alın.

2. Dosyaları *vsct.exe* derleyicisi ile aynı dizine yerleştirin.

3. Visual Studio komut isteminde *. CTO* ve *. ctsyd* dosyalarını içeren dizine gidin.

4. Tür

    ```
    vsct.exe <ctofilename>.cto <vsctfilename>.vsct -S<symfilename>.ctsym
    ```

     Burada \<ctofilename\> *. CTO* dosyasının adı, \<vsctfilename\> oluşturmak istediğiniz *. vsct* dosyasının adıdır ve \<symfilename\> *. ctsyd* dosyasının adıdır.

     Bu işlem yeni bir *. vsct* XML komut tablosu derleyici dosyası oluşturur. Dosyayı herhangi bir *. vsct* dosyası gibi *vsct.exe*, vsct derleyicisi ile düzenleyebilir ve derleyebilirsiniz.

## <a name="compile-the-code"></a>Kodu derle
 Yalnızca bir *. vsct* dosyasını bir projeye eklemek, derlemeye neden olmaz. Yapı sürecinde bu dosyayı eklemeniz gerekir.

### <a name="to-add-a-vsct-file-to-project-compilation"></a>Proje derlemesine bir. vsct dosyası eklemek için

1. Proje dosyanızı düzenleyicide açın. Proje yüklüyse, önce onu kaldırmanız gerekir.

2. Aşağıdaki örnekte gösterildiği gibi, bir öğesi içeren bir [ItemGroup öğesi](../../msbuild/itemgroup-element-msbuild.md) ekleyin `VSCTCompile` .

    ```xml
    <ItemGroup>
      <VSCTCompile Include="TopLevelMenu.vsct">
        <ResourceName>Menus.ctmenu</ResourceName>
      </VSCTCompile>
    </ItemGroup>

    ```

     `ResourceName`Öğesi her zaman olarak ayarlanmalıdır `Menus.ctmenu` .

3. Projeniz bir *. resx* dosyası içeriyorsa, `EmbeddedResource` `MergeWithCTO` Aşağıdaki örnekte gösterildiği gibi bir öğesi içeren bir öğesi ekleyin:

    ```xml
    <EmbeddedResource Include="VSPackage.resx">
      <MergeWithCTO>true</MergeWithCTO>
      <ManifestResourceName>VSPackage</ManifestResourceName>
    </EmbeddedResource>

    ```

     Bu biçimlendirme, `ItemGroup` gömülü kaynakları içeren öğenin içinde olmalıdır.

4. Düzenleyicide, genellikle * \<ProjectName\> Package.cs* veya * \<ProjectName\> Package. vb*adlı paket dosyasını açın.

5. `ProvideMenuResource`Aşağıdaki örnekte gösterildiği gibi, Package sınıfına bir öznitelik ekleyin.

    ```csharp
    [ProvideMenuResource("Menus.ctmenu", 1)]
    ```

     İlk parametre değeri `ResourceName` Proje dosyasında tanımladığınız özniteliğin değeriyle eşleşmelidir.

## <a name="see-also"></a>Ayrıca bkz.
- [Author. vsct dosyaları](../../extensibility/internals/authoring-dot-vsct-files.md)
- [Visual Studio komut tablosu (. vsct) dosyaları](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [VSCT XML Şeması Başvurusu](../../extensibility/vsct-xml-schema-reference.md)
