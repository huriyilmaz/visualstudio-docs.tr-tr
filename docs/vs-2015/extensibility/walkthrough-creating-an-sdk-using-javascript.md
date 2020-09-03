---
title: 'İzlenecek yol: JavaScript kullanarak SDK oluşturma | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: a8c89d5d-5b78-4435-817f-c5f25ca6d715
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3e953d9051b9bc7e95dc29e02eb580c4d93fca26
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68148825"
---
# <a name="walkthrough-creating-an-sdk-using-javascript"></a>İzlenecek Yol: JavaScript Kullanarak SDK Oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu izlenecek yol, Visual Studio uzantısı (VSıX) olarak basit bir matematik SDK 'Sı oluşturmak için JavaScript 'ı nasıl kullanacağınızı öğretir.  İzlenecek yol aşağıdaki bölümlere ayrılmıştır:  
  
- [SimpleMathVSIX Extension SDK projesini oluşturmak için](../extensibility/walkthrough-creating-an-sdk-using-javascript.md#createSimpleMathVSIX)  
  
- [SDK 'Yı kullanan bir örnek uygulama oluşturmak için](../extensibility/walkthrough-creating-an-sdk-using-javascript.md#createSampleApp)  
  
  JavaScript için, hiçbir sınıf kitaplığı proje türü yoktur. Bu kılavuzda örnek arithmetic.js dosyası doğrudan VSıX projesinde oluşturulur. Uygulamada, önce JavaScript ve CSS dosyalarını bir Windows Mağazası uygulaması olarak derleyip test etmenizi öneririz — Örneğin, **boş uygulama** şablonunu kullanarak, bir VSIX projesine yerleştirmelisiniz.  
  
## <a name="prerequisites"></a>Ön koşullar  
 Bu yönergeyi izlemek için, Visual Studio SDK 'sını yüklemelisiniz. Daha fazla bilgi için bkz. [Visual STUDIO SDK](../extensibility/visual-studio-sdk.md).  
  
## <a name="to-create-the-simplemathvsix-extension-sdk-project"></a><a name="createSimpleMathVSIX"></a> SimpleMathVSIX Extension SDK projesini oluşturmak için  
  
1. Menü çubuğunda **Dosya**, **Yeni**, **Proje**' yi seçin.  
  
2. Şablon kategorileri listesinde, **Visual C#** altında **genişletilebilirlik**' i seçin ve **VSIX proje** şablonu ' nu seçin.  
  
3. **Ad** metin kutusunda, belirtin `SimpleMathVSIX` ve **Tamam** düğmesini seçin.  
  
4. **Visual Studio paket Sihirbazı** görünürse, **hoş geldiniz** sayfasında **Ileri** düğmesini seçin ve ardından **sayfa 1/7**' de **son** düğmesini seçin.  
  
     **Bildirim Tasarımcısı** açılarak, bildirim dosyasını doğrudan değiştirerek bu yönergeyi basit tutacağız.  
  
5. **Çözüm Gezgini**, Source. Extension. valtmanifest dosyası için kısayol menüsünü açın ve **kodu görüntüle**' yi seçin. Dosyadaki mevcut içeriği değiştirmek için bu kodu kullanın.  
  
    ```  
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
  
6. **Çözüm Gezgini**' de, SimpleMathVSIX projesi için kısayol menüsünü açın ve **Ekle**, **Yeni öğe**' yi seçin.  
  
7. **Veri** kategorisinde, **XML dosyası**' nı seçin, dosyayı adlandırın `SDKManifest.xml` ve **Ekle** düğmesini seçin.  
  
8. **Çözüm Gezgini**' de, SDKManifest.xml dosyası için kısayol menüsünü açın ve sonra dosyayı **XML düzenleyicisinde**göstermek için **Aç** ' ı seçin.  
  
9. SDKManifest.xml dosyasına aşağıdaki kodu ekleyin.  
  
    ```  
    <?xml version="1.0" encoding="utf-8" ?>  
    <FileList  
      DisplayName="Simple Math"  
      MinVSVersion="14.0"  
      AppliesTo="JavaScript+WindowsAppContainer"  
      SupportsMultipleVersions="Error"  
      MoreInfo="http://www.msdn.microsoft.com/">  
  
      <!-- JS -->  
      <File Content="js\arithmetic.js" />  
    </FileList>  
  
    ```  
  
10. **Çözüm Gezgini**SDKManifest.xml dosyanın kısayol menüsünde **Özellikler**' i seçin.  
  
11. **Özellikler** penceresinde **VSIX Içindeki içerme** özelliğini **doğru**olarak ayarlayın.  
  
12. **Çözüm Gezgini**, SimpleMathVSIX projesinin kısayol menüsünde, **Ekle**, **Yeni klasör**' i seçin ve klasörü adlandırın `Redist` .  
  
13. Bu klasör yapısını oluşturmak için Redist altında alt klasörler ekleyin:  
  
     \Redist\CommonConfiguration\Neutral\SimpleMath\js\  
  
14. \Js\ klasörünün kısayol menüsünde, **Ekle**, **Yeni öğe**' yi seçin.  
  
15. **Visual C# öğeleri**altında **Web** kategorisini seçin ve sonra **JavaScript dosya** öğesini seçin. Dosyayı adlandırın `arithmetic.js` ve ardından **Ekle** düğmesini seçin.  
  
16. Aşağıdaki kodu arithmetic.js ekleyin:  
  
    ```  
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
  
17. **Çözüm Gezgini**arithmetic.js dosyanın kısayol menüsünde **Özellikler**' i seçin. Bu özellik değişikliklerini yapın:  
  
    - **VSIX 'Te Include** özelliğini **true**olarak ayarlayın.  
  
    - **Çıkış Dizinine Kopyala** özelliğini **her zaman Kopyala**olarak ayarlayın.  
  
18. **Çözüm Gezgini**, SimpleMathVSIX projesinin kısayol menüsünde, **Oluştur**' u seçin.  
  
19. Yapı başarıyla tamamlandıktan sonra, proje için kısayol menüsünde **klasörü dosya Gezgini 'Nde aç**' ı seçin. \Bin\Debug dizinine gidin \\ ve `SimpleMathVSIX.vsix` uygulamayı yüklemek için çalıştırın.  
  
20. **Yükleme düğmesini seçin** ve yüklemenin tamamlanmasını sağlayın.  
  
21. Visual Studio’yu yeniden başlatın.  
  
## <a name="to-create-a-sample-app-that-uses-the-sdk"></a><a name="createSampleApp"></a> SDK 'Yı kullanan bir örnek uygulama oluşturmak için  
  
1. Menü çubuğunda **Dosya**, **Yeni**, **Proje**' yi seçin.  
  
2. Şablon kategorileri listesinde, **JavaScript**altında **Windows Mağazası**' nı seçin ve **boş uygulama** şablonunu seçin.  
  
3. **Ad** kutusunda, öğesini belirtin `ArithmeticUI` . **Tamam** düğmesini seçin.  
  
4. **Çözüm Gezgini**' de, ArithmeticUI projesi için kısayol menüsünü açın ve **Ekle**, **başvuru**' yı seçin.  
  
5. **Windows**altında, **Uzantılar**' ı seçin ve **basit matematik** ' ın görüntülendiğini unutmayın.  
  
6. **Basit matematik** onay kutusunu seçin ve ardından **Tamam** düğmesini seçin.  
  
7. **Çözüm Gezgini**, **Başvurular**altında **basit matematik** başvurusunun görüntülendiğini unutmayın. Genişletin ve arithmetic.js içeren bir \js\ klasörü olduğuna dikkat edin. Kaynak kodunuzun yüklendiğini onaylamak için arithmetic.js açabilirsiniz.  
  
8. default.htm içeriğini değiştirmek için aşağıdaki kodu kullanın.  
  
    ```  
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
  
9. \js\default.js içeriğini değiştirmek için sonraki kodu kullanın.  
  
    ```  
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
  
10. \Css\default.exe içeriğini şu kodla değiştirin:  
  
    ```  
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
  
11. Uygulamayı derlemek ve çalıştırmak için F5 tuşunu seçin.  
  
12. Uygulama kullanıcı arabiriminde iki sayı girin, bir işlem seçin ve ardından **=** düğmeyi seçin. Doğru sonuç görüntülenir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yazılık Geliştirme Seti Oluşturma](../extensibility/creating-a-software-development-kit.md)
