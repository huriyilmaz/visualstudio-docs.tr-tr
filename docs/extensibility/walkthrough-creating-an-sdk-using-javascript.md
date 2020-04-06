---
title: 'Walkthrough: JavaScript kullanarak Bir SDK oluşturma | Microsoft Dokümanlar'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: a8c89d5d-5b78-4435-817f-c5f25ca6d715
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f3a3fa110bd6521443521449898474299dd267d6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697501"
---
# <a name="walkthrough-create-an-sdk-using-javascript"></a>Walkthrough: JavaScript kullanarak bir SDK oluşturma
Bu walkthrough visual Studio Extension (VSIX) olarak basit bir matematik SDK oluşturmak için JavaScript nasıl kullanılacağını öğretir.  Walkthrough şu bölümlere ayrılmıştır:

- [SimpleMathVSIX uzantısı SDK projesini oluşturmak için](../extensibility/walkthrough-creating-an-sdk-using-javascript.md#createSimpleMathVSIX)

- [SDK kullanan örnek bir uygulama oluşturmak için](../extensibility/walkthrough-creating-an-sdk-using-javascript.md#createSampleApp)

  JavaScript için sınıf kitaplığı proje türü yoktur. Bu gözden geçirme de, örnek *aritmetik.js* dosyası doğrudan VSIX projesinde oluşturulur. Uygulamada, javascript ve CSS dosyalarını bir VSIX projesine koymadan önce **Boş Uygulama** şablonu kullanarak bir Windows Mağazası uygulaması olarak oluşturmanızı ve test etmelerini öneririz.

## <a name="prerequisites"></a>Ön koşullar
 Bu izlenmeyi takip etmek için Visual Studio SDK'yı yüklemeniz gerekir. Daha fazla bilgi için [Visual Studio SDK'ya](../extensibility/visual-studio-sdk.md)bakın.

## <a name="to-create-the-simplemathvsix-extension-sdk-project"></a><a name="createSimpleMathVSIX"></a>SimpleMathVSIX uzantısı SDK projesini oluşturmak için

1. Menü çubuğunda**Yeni** > **Proje** **yi seçin.** > 

2. Şablon kategorileri listesinde, **Visual C#** altında, **Genişletilebilirliği**seçin ve ardından **VSIX Project şablonunu** seçin.

3. **Ad** metin kutusunda Tamam `SimpleMathVSIX` **düğmesini** belirtin ve seçin.

4. Visual **Studio Paket Sihirbazı** görünürse, **Hoş Geldiniz** **sayfasındaki Sonraki** düğmesini seçin ve ardından **7'nin Sayfa**1'inde **Finish** düğmesini seçin.

     Manifest **Designer** açılsa da, doğrudan manifesto dosyasını değiştirerek bu gözden geçirme yi basit tutacağız.

5. **Solution Explorer'da** **source.extension.vsixmanifest** dosyasının kısayol menüsünü açın ve ardından **Kodu Görüntüle'yi**seçin. Dosyadaki varolan içeriği değiştirmek için bu kodu kullanın.

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <PackageManifest Version="2.0.0" xmlns="http://schemas.microsoft.com/developer/vsx-schema/2011" xmlns:d="http://schemas.microsoft.com/developer/vsx-schema-design/2011">
      <Metadata>
        <Identity Id="SimpleMathVSIX" Version="1.0" Language="en-US" Publisher="myname" />
        <DisplayName>Simple Math</DisplayName>
        <Description>Does basic arithmetic calculations.</Description>
      </Metadata>
      <Installation Scope="Global" AllUsers="true">
        <InstallationTarget Id="Microsoft.ExtensionSDK" TargetPlatformIdentifier="Windows" TargetPlatformVersion="v8.0" SdkName="SimpleMath" SdkVersion="1.0" />
      </Installation>
      <Dependencies>
        <Dependency Id="Microsoft.Framework.NDP" DisplayName="Microsoft .NET Framework" d:Source="Manual" Version="4.5" />
      </Dependencies>
      <Assets>
        <Asset Type="Microsoft.ExtensionSDK" d:Source="File" Path="SDKManifest.xml" />
      </Assets>
    </PackageManifest>
    ```

6. **Solution Explorer'da** **SimpleMathVSIX** projesinin kısayol menüsünü açın ve ardından**Yeni Öğe** **Ekle'yi** > seçin.

7. **Veri** **kategorisinde, XML dosyasını**seçin, `SDKManifest.xml`dosyayı adlandırın ve **Ekle** düğmesini seçin.

8. **Solution**Explorer'da, **SDKManifest.xml** dosyasının kısayol menüsünü açın ve ardından dosyayı **XML Düzenleyicisi'nde**görüntülemek için **Aç'ı** seçin.

9. **SDKManifest.xml** dosyasına aşağıdaki kodu ekleyin.

    ```xml
    <?xml version="1.0" encoding="utf-8" ?>
    <FileList
      DisplayName="Simple Math"
      MinVSVersion="14.0"
      AppliesTo="JavaScript+WindowsAppContainer"
      SupportsMultipleVersions="Error"
      MoreInfo="https://msdn.microsoft.com/">

      <!-- JS -->
      <File Content="js\arithmetic.js" />
    </FileList>

    ```

10. **Çözüm Gezgini'nde,** **SDKManifest.xml** dosyasının kısayol menüsünde **Özellikler'i**seçin.

11. **Özellikler** penceresinde, **VSIX özelliğine Ekle'yi** **True**olarak ayarlayın.

12. **Solution Explorer'da,** **SimpleMathVSIX** projesinin kısayol menüsünde Yeni**Klasör** **Ekle'yi** > seçin ve ardından klasörü `Redist`adlandırın.

13. Bu klasör yapısını oluşturmak için Redist'in altına alt klasörler ekleyin:

     *\Redist\CommonConfiguration\Neutral\SimpleMath\js\\*

14. **\\ \js** klasörünün kısayol menüsünde**Yeni Öğe** **Ekle'yi** > seçin.

15. **Visual C# öğelerinin** **altında, Web** kategorisini seçin ve ardından **JavaScript Dosya** öğesini seçin. Dosyayı `arithmetic.js`adlandırın ve sonra **Ekle** düğmesini seçin.

16. Aşağıdaki kodu *aritmetik.js'ye*ekleyin:

    ```csharp
    (function (global) {
        "use strict";
        global.Arithmetic = {
            add: function (firstNumber, secondNumber) {
                return firstNumber + secondNumber;
            },

            subtract: function (firstNumber, secondNumber) {
                return firstNumber - secondNumber;
            },

            multiply: function (firstNumber, secondNumber) {
                return firstNumber * secondNumber;
            },

            divide: function (firstNumber, secondNumber) {
                return firstNumber / secondNumber;
            }
        };
    })(this);

    ```

17. **Çözüm Gezgini'nde,** **aritmetik.js** dosyasının kısayol menüsünde **Özellikler'i**seçin. Bu özellik değişikliklerini yapın:

    - **VSIX özelliğine Ekle'yi** **True**olarak ayarlayın.

    - **Copy'yi Çıkış Dizini özelliğine** her **zaman kopyalamak**için ayarlayın.

18. **Solution Explorer'da** **SimpleMathVSIX** projesinin kısayol menüsünde **Oluştur'u**seçin.

19. Yapı başarıyla tamamlandıktan sonra, projenin kısayol menüsünde **Dosya Gezgini'nde Klasörü Aç'ı**seçin. **\bin\debug'a\\**gidin `SimpleMathVSIX.vsix` ve yüklemek için çalıştırın.

20. **Yükle** düğmesini seçin ve yüklemenin tamamlanmasına izin verin.

21. Visual Studio'yu yeniden başlatın.

## <a name="to-create-a-sample-app-that-uses-the-sdk"></a><a name="createSampleApp"></a>SDK kullanan örnek bir uygulama oluşturmak için

1. Menü çubuğunda**Yeni** > **Proje** **yi seçin.** > 

2. Şablon kategorileri listesinde, **JavaScript** **altında, Windows Mağazası'nı**seçin ve ardından **Boş Uygulama** şablonu'nu seçin.

3. **Ad** kutusunda, belirtin. `ArithmeticUI` **Tamam** düğmesini seçin.

4. **Çözüm Gezgini'nde,** **AritmetikUI** projesinin kısayol menüsünü açın ve ardından**Başvuru** **Ekle'yi** > seçin.

5. **Windows'un**altında **Uzantılar'ı**seçin ve **Basit Matematik'in** görüntülendiğini unutmayın.

6. Basit **Matematik** onay kutusunu seçin ve ardından **Tamam** düğmesini seçin.

7. **Solution**Explorer'da, **Referanslar**altında, **Basit Matematik** başvurusu görüntülendiğinden dikkat edin. Genişletin ve **aritmetik.js**içeren bir **\js\\ ** klasörü olduğunu unutmayın. Kaynak kodunuzun yüklü olduğunu doğrulamak için **aritmetik.js'yi** açabilirsiniz.

8. *default.htm*içeriğini değiştirmek için aşağıdaki kodu kullanın.

   ```html
   <!DOCTYPE html>
   <html>
   <head>
       <meta charset="utf-8" />
       <title>ArithmeticUI</title>

       <!-- WinJS references -->
       <link href="//Microsoft.WinJS.1.0/css/ui-dark.css" rel="stylesheet" />
       <script src="//Microsoft.WinJS.1.0/js/base.js"></script>
       <script src="//Microsoft.WinJS.1.0/js/ui.js"></script>

       <!-- ArithmeticUI references -->
       <link href="/css/default.css" rel="stylesheet" />
       <script src="/js/default.js"></script>
       <script src="/SimpleMath/js/arithmetic.js"></script>
   </head>
   <body>
       <form>
       <div id="calculator" class="ms-grid">
           <input name="firstNumber" id="firstNumber" type="number" step="any">
           <div id="operators">
               <button class="operator" type="button">+</button>
               <button class="operator" type="button">-</button>
               <button class="operator" type="button">*</button>
               <button class="operator" type="button">/</button>
           </div>
           <input id="secondNumber" type="number">
           <button class="calculate" type="button">=</button>
           <input id="result" type="number" name="result" disabled="" readonly="">
       </div>
       </form>
   </body>
   </html>
   ```

9. *\js\default.js*içeriğini değiştirmek için aşağıdaki kodu kullanın.

    ```csharp
    (function () {
        "use strict";

        var app = WinJS.Application;
        var operation = null;

        function calculateResult() {
            var firstNumber = parseFloat(document.querySelector("#firstNumber").value),
                secondNumber = parseFloat(document.querySelector("#secondNumber").value),
                result = 0;

            if (isNaN(firstNumber) || isNaN(secondNumber)) {
                result = 0;
            }
            else {
                switch (operation) {
                    case "+":
                        result = Arithmetic.add(firstNumber, secondNumber);
                        break;
                    case "-":
                        result = Arithmetic.subtract(firstNumber, secondNumber);
                        break;
                    case "*":
                        result = Arithmetic.multiply(firstNumber, secondNumber);
                        break;
                    case "/":
                        result = Arithmetic.divide(firstNumber, secondNumber);
                        break;
                    default:
                }
            }
            document.querySelector("#result").value = result.toString();
        }

        app.onactivated = function (args) {
            document.querySelector("#calculator").addEventListener("click", function (event) {
                if (event.target.tagName.toLowerCase() === "button") {
                    switch (event.target.className) {
                        case "operator":
                            operation = event.target.innerText;
                            break;
                        case "calculate":
                            calculateResult();
                            break;
                        default:
                            break;
                    }
                }
            });
        };

        app.start();
    })();
    ```

10. *\css\default.css* içeriğini bu kodla değiştirin:

    ```xml
    form {
        display: -ms-grid;
        -ms-grid-rows: 1fr auto 1fr;
        -ms-grid-columns: 1fr auto 1fr;
        height: 100%;
        width: 100%;
    }

    button, input[type=number] {
        margin-right: 5px;
        -ms-grid-row-align: center;
    }

    #calculator {
        -ms-grid-column: 2;
        -ms-grid-row: 2;
        display: -ms-grid;
        -ms-grid-rows: 1fr;
        -ms-grid-columns: auto min-content auto auto auto;
    }

    .ms-grid input {
        width: 5em;
    }

    #firstNumber {
        -ms-grid-column: 1;
        -ms-grid-row-align: center;
    }

    #operators {
        -ms-grid-column: 2;
        -ms-grid-row-align: center;
    }

        #operators button.operator {
            margin-bottom: 5px;
            height: 40px;
        }

    #secondNumber {
        -ms-grid-column: 3;
    }

    button.calculate {
        -ms-grid-column: 4;
        -ms-grid-row-align: center;
        height: 40px;
    }

    #result {
        -ms-grid-column: 5;
    }

    ```

11. Uygulamayı oluşturmak ve çalıştırmak için **F5** tuşunu seçin.

12. Uygulama UI'sinde, herhangi iki sayı girin, bir **=** işlem seçin ve ardından düğmeyi seçin. Doğru sonuç görüntülenir.

## <a name="see-also"></a>Ayrıca bkz.
- [Yazılık Geliştirme Seti Oluşturma](../extensibility/creating-a-software-development-kit.md)
