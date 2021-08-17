---
title: 'Adım adım kılavuz: JavaScript komutlarını kullanarak SDK | Microsoft Docs'
description: Bu izlenecek yolu kullanarak JavaScript'i kullanarak Visual Studio Uzantısı olarak basit bir matematik SDK'sı oluşturma hakkında bilgi edinebilirsiniz.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: a8c89d5d-5b78-4435-817f-c5f25ca6d715
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 3fdbf8b097c2e71341abc43ccb3e975392e1f810
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122056647"
---
# <a name="walkthrough-create-an-sdk-using-javascript"></a>Adım adım kılavuz: JavaScript kullanarak SDK oluşturma
Bu kılavuzda JavaScript kullanarak basit bir matematik SDK'sı oluşturma ve Visual Studio (VSIX) öğretildi.  Kılavuz şu bölümlere ayrılmıştır:

- [SimpleMathVSIX uzantısı SDK projesi oluşturmak için](../extensibility/walkthrough-creating-an-sdk-using-javascript.md#createSimpleMathVSIX)

- [SDK'yı kullanan örnek bir uygulama oluşturmak için](../extensibility/walkthrough-creating-an-sdk-using-javascript.md#createSampleApp)

  JavaScript için sınıf kitaplığı proje türü yoktur. Bu kılavuzda, örnek *arithmetic.js* dosyası doğrudan VSIX projesinde oluşturulur. Uygulamada, vsIX projesine eklemeden önce JavaScript ve CSS dosyalarını bir Windows Store uygulaması olarak  (örneğin, Boş Uygulama şablonunu kullanarak) derlemenizi ve testnizi öneririz.

## <a name="prerequisites"></a>Önkoşullar
 Bu izlenecek yolu takip etmek için Visual Studio SDK'sı yüklemeniz gerekir. Daha fazla bilgi için [bkz. Visual Studio SDK.](../extensibility/visual-studio-sdk.md)

## <a name="to-create-the-simplemathvsix-extension-sdk-project"></a><a name="createSimpleMathVSIX"></a> SimpleMathVSIX uzantısı SDK projesi oluşturmak için

1. Menü çubuğunda Dosya Yeni **dosya'Project.**  >    >  

2. Şablon kategorileri listesinde, **Visual C#** altında **Genişletilebilirlik'i seçin** ve ardından **VSIX** Project seçin.

3. Ad **metin** kutusunda Tamam `SimpleMathVSIX` düğmesini  belirtin ve seçin.

4. Paket **Visual Studio açılırsa** Hoş Geldiniz  sayfasındaki Sonraki  düğmesini seçin ve ardından **7. Sayfa 1'de** Son **düğmesini** seçin.

     Bildirim **Tasarımcısı açsa** da, bildirim dosyasını doğrudan değiştirerek bu izlenecek yolu basit tutabilirsiniz.

5. Bu **Çözüm Gezgini** **source.extension.vsixmanifest** dosyasının kısayol menüsünü açın ve Ardından Kodu Görüntüle'yi **seçin.** Dosyada mevcut içeriği değiştirmek için bu kodu kullanın.

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

6. Bu **Çözüm Gezgini** **SimpleMathVSIX** projesinin kısayol menüsünü açın ve Yeni Öğe **Ekle'yi**  >  **seçin.**

7. Veri **kategorisinde** **XML** dosyasını seçin, dosyayı olarak adlandır `SDKManifest.xml` ve Ekle **düğmesini** seçin.

8. Bu **Çözüm Gezgini,** dosyanın kısayol **SDKManifest.xml** açın ve dosyayı XML  Düzenleyicisi'nde görüntülemek için Aç'ı **seçin.**

9. Aşağıdaki koduSDKManifest.xml **ekleyin.**

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

10. Çözüm Gezgini dosyasındaki kısayol menüsünde **Özellikler'SDKManifest.xml** **seçin.**

11. Özellikler **penceresinde** **VSIX özelliğine dahil edin özelliğini** True olarak **ayarlayın.**

12. Bu **Çözüm Gezgini** **SimpleMathVSIX** projesinin kısayol menüsünde Yeni Klasör Ekle'yi seçin ve  >  klasöre adını `Redist` girin.

13. Bu klasör yapısını oluşturmak için Redist altına alt klasörler ekleyin:

     *\Redist\CommonConfiguration\Neutral\SimpleMath\js\\*

14. **\js \\** klasörünün kısayol menüsünde Yeni Öğe **Ekle'yi**  >  **seçin.**

15. **Visual C# öğeleri** altında Web **kategorisini** ve ardından **JavaScript Dosyası öğesini** seçin. Dosyaya adını `arithmetic.js` ve ardından Ekle **düğmesini** seçin.

16. aşağıdaki kodu *arithmetic.js:*

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

17. Çözüm Gezgini dosyasındaki kısayol menüsünde **Özellikler'arithmetic.js** **seçin.** Şu özellik değişikliklerini yapın:

    - **VSIX'e Dahil Edin özelliğini** True olarak **ayarlayın.**

    - Çıkış **Dizinine Kopyala özelliğini Her Zaman** Kopyala olarak **ayarlayın.**

18. Bu **Çözüm Gezgini** **SimpleMathVSIX** projesinin kısayol menüsünde Oluştur'a **tıklayın.**

19. Derleme başarıyla tamamlandıktan sonra, projenin kısayol menüsünde klasör içinde Klasör **Aç'ı Dosya Gezgini.** **\bin\debug dizinine gidin \\** ve yüklemek için `SimpleMathVSIX.vsix` çalıştırın.

20. Yükle **düğmesini seçin** ve yüklemenin tamamlanır.

21. Visual Studio’yu yeniden başlatın.

## <a name="to-create-a-sample-app-that-uses-the-sdk"></a><a name="createSampleApp"></a> SDK'yı kullanan örnek bir uygulama oluşturmak için

1. Menü çubuğunda Dosya Yeni **dosya'Project.**  >    >  

2. Şablon kategorileri listesinde, **JavaScript'in** altında Windows **Store'a** tıklayın ve ardından Boş Uygulama **şablonunu** seçin.

3. Ad **kutusunda** `ArithmeticUI` belirtin. Tamam **düğmesini** seçin.

4. Bu **Çözüm Gezgini,** **AritmetikUI projesinin kısayol menüsünü** açın ve Başvuru Ekle'yi   >  **seçin.**

5. Aşağıdaki **Windows** **Uzantılar'ı seçin** ve Basit Matematik'in **görüntülendiğinden dikkatin.**

6. Basit Matematik **onay** kutusunu ve ardından Tamam **düğmesini** seçin.

7. Bu **Çözüm Gezgini,** **Başvurular altında** Basit Matematik **başvurusu'nın görüntülendiğinden** dikkatin. Genişletin ve dosya içeren bir **\js \\** klasörü olduğunuarithmetic.js. **** Kaynak **kodunuzunarithmetic.js** onaylamak için bu dosyayı açabilirsiniz.

8. aşağıdaki kodu kullanarak dosyanın içeriğini *default.htm.*

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

9. aşağıdaki kodu kullanarak dosyanın içeriğini *\js\default.js.*

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

10. *\css\default.css içeriğini şu* kodla değiştirin:

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

11. Uygulamayı **derlemek ve** çalıştırmak için F5 anahtarını seçin.

12. Uygulama kullanıcı arabiriminde iki sayı girin, bir işlem seçin ve düğmeyi **=** seçin. Doğru sonuç görüntülenir.

## <a name="see-also"></a>Ayrıca bkz.
- [Yazılık Geliştirme Seti Oluşturma](../extensibility/creating-a-software-development-kit.md)
