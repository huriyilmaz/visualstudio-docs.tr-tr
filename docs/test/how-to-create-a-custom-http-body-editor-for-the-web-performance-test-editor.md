---
title: Web performans testi için HTTP Gövde Düzenleyicisi oluşturma
description: Bir Web hizmeti isteğinin dize gövde içeriğini veya ikili gövde içeriğini düzenlemenizi sağlayan özel bir İçerik Düzenleyicisi oluşturmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- Web performance tests, custom HTTP body editor
ms.assetid: a0b2d8ff-3e2a-487e-9172-90047174f336
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.openlocfilehash: e096333d66fffd233bfb4b9de7f40e18f1277846
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99966740"
---
# <a name="how-to-create-a-custom-http-body-editor-for-the-web-performance-test-editor"></a>Nasıl yapılır: Web Performans Testi Düzenleyicisi için özel HTTP Gövde Düzenleyicisi oluşturma

Dize gövdesi içeriğini veya bir Web hizmeti isteğinin ikili gövde içeriğini (örneğin, SOAP, REST, asmx, WCF, RıA ve diğer Web hizmeti istek türleri) düzenlemenizi sağlayan özel bir İçerik Düzenleyicisi oluşturabilirsiniz.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Bu tür düzenleyicilerin uygulanması için:

- **Dize İçerik Düzenleyicisi** Bu, arabirimi kullanılarak uygulanır <xref:Microsoft.VisualStudio.TestTools.WebTesting.IStringHttpBodyEditorPlugin> .

- **İkili içerik Düzenleyicisi** Bu, arabirimi kullanılarak uygulanır <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin> .

Bu arabirimler ad alanında yer alır <xref:Microsoft.VisualStudio.TestTools.WebTesting> .

## <a name="create-a-windows-control-library-project"></a>Windows Denetim Kitaplığı projesi oluşturma

1. Visual Studio 'da yeni bir **Windows Forms denetim kitaplığı** projesi oluşturun. Proje **Messagedüzenleyicilerini** adlandırın.

   Proje yeni çözüme eklenir ve <xref:System.Windows.Forms.UserControl> Tasarımcı içinde adlandırılmış bir *UserControl1.cs* sunulur.

1. **Araç kutusundan**, **ortak denetimler** kategorisi altında, <xref:System.Windows.Forms.RichTextBox> UserControl1 yüzeyine sürükleyin.

1. ![Denetimin sağ üst köşesinde bulunan eylem etiketi glifini (akıllı etiket karakter ](../test/media/vs_winformsmttagglyph.gif) ) seçin <xref:System.Windows.Forms.RichTextBox> ve sonra **üst kapsayıcıda yerleştir**' i seçin.

1. **Çözüm Gezgini**, Windows Forms kitaplığı projesine sağ tıklayın ve **Özellikler**' i seçin.

1. **Özellikler**' de **uygulama** sekmesini seçin.

1. **Hedef çerçeve** açılan listesinde .NET Framework 4 (veya üzeri) öğesini seçin.

1. **Hedef çerçeve değişimi** iletişim kutusu görüntülenir.

1. **Evet**' i seçin.

1. **Çözüm Gezgini**, **Başvurular** düğümüne sağ tıklayın ve **Başvuru Ekle**' yi seçin.

1. **Başvuru Ekle** iletişim kutusu görüntülenir.

1. Öğesini seçin. **Net** Tab, aşağı kaydırın ve **Microsoft. VisualStudio. QualityTools. WebTestFramework** ' ı seçin ve ardından **Tamam**' ı seçin.

1. **Görünüm Tasarımcısı** hala açık değilse, **Çözüm Gezgini**' de, **UserControl1.cs** ' a sağ tıklayın ve ardından **tasarımcıyı görüntüle**' yi seçin.

1. Tasarım yüzeyinde sağ tıklayıp **kodu görüntüle**' yi seçin.

1. Seçim Sınıf adını ve oluşturucuyu, örnek olarak, MessageEditorControl gibi anlamlı bir adla değiştirin:

    > [!NOTE]
    > Örnek MessageEditorControl kullanır.

    ```csharp
    namespace MessageEditors
    {
        public partial class MessageEditorControl : UserControl
        {
            public MessageEditorControl()
            {
                InitializeComponent();
            }
        }
    }
    ```

1. RichTextBox1 içinde metin almayı ve ayarlamayı etkinleştirmek için aşağıdaki özellikleri ekleyin. <xref:Microsoft.VisualStudio.TestTools.WebTesting.IStringHttpBodyEditorPlugin>Arabirim EditString kullanır ve <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin> EditByteArray kullanır:

    ```csharp
    public String EditString
    {
       get
       {
           return this.richTextBox1.Text;
       }
       set
       {
           this.richTextBox1.Text = value;
       }
    }

    public byte[] EditByteArray
    {
       get
       {
           return System.Convert.FromBase64String(richTextBox1.Text);
       }
       set
       {
           richTextBox1.Text = System.Convert.ToBase64String(value, 0, value.Length);
       }
    }
    ```

## <a name="add-a-class-to-the-windows-control-library-project"></a>Windows denetim kitaplığı projesine bir sınıf ekleme

Projeye bir sınıf ekleyin. Ve arabirimlerini uygulamak için kullanılacaktır <xref:Microsoft.VisualStudio.TestTools.WebTesting.IStringHttpBodyEditorPlugin> <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin> .

**Bu yordamdaki koda genel bakış**

<xref:System.Windows.Forms.UserControl>Önceki yordamda oluşturulan messageEditorControl MessageEditorControl olarak oluşturulur:

```csharp
private MessageEditorControl messageEditorControl
```

MessageEditorControl örneği, yöntemi tarafından oluşturulan eklenti iletişim kutusunda barındırılır <xref:Microsoft.VisualStudio.TestTools.WebTesting.IStringHttpBodyEditorPlugin.CreateEditor*> . Ek olarak, messageEditorControl <xref:System.Windows.Forms.RichTextBox> , içindeki içeriğiyle doldurulur <xref:Microsoft.VisualStudio.TestTools.WebTesting.IHttpBody> . Ancak, döndürülmediği takdirde eklenti oluşturma gerçekleşemez <xref:Microsoft.VisualStudio.TestTools.WebTesting.IStringHttpBodyEditorPlugin.SupportsContentType*> `true` . Bu düzenleyici söz konusu olduğunda, <xref:Microsoft.VisualStudio.TestTools.WebTesting.IStringHttpBodyEditorPlugin.SupportsContentType*> içinde ' `true` <xref:Microsoft.VisualStudio.TestTools.WebTesting.IHttpBody.ContentType*> XML ' varsa ' ı döndürür <xref:Microsoft.VisualStudio.TestTools.WebTesting.IHttpBody> .

Dize gövdesinin düzenlenmesi tamamlandığında ve Kullanıcı eklenti iletişim kutusunda **Tamam** ' ı tıklattığında, <xref:Microsoft.VisualStudio.TestTools.WebTesting.IStringHttpBodyEditorPlugin.GetNewValue*> düzenlenmiş metni bir dize olarak almak ve Web test performansı Düzenleyicisi 'Ndeki istekteki **dize gövdesini** güncelleştirmek için çağırılır.

### <a name="create-a-class-and-implement-the-istringhttpbodyeditorplugin-interface"></a>Bir sınıf oluşturun ve ıtringhttpbodyeditorplugin arabirimini uygulayın

1. **Çözüm Gezgini**' de, Windows Forms denetim kitaplığı projesine sağ tıklayın ve **Yeni öğe Ekle**' yi seçin.

   **Yeni Öğe Ekle** iletişim kutusu görüntülenir.

2. **Sınıf** seçin.

3. **Ad** metin kutusuna sınıf için anlamlı bir ad yazın, örneğin, `MessageEditorPlugins` .

4. **Ekle**' yi seçin.

   Class1 projeye eklenir ve kod düzenleyicisinde sunulur.

5. Kod Düzenleyicisi 'nde aşağıdaki `using` ifadeyi ekleyin:

    ```csharp
    using Microsoft.VisualStudio.TestTools.WebTesting;
    ```

6. Arabirimi uygulamak için aşağıdaki kodu yapıştırın:

    ```csharp
    /// <summary>
    /// Editor for generic text based hierarchical messages such as XML and JSON.
    /// </summary>
    public class XmlMessageEditor : IStringHttpBodyEditorPlugin
    {
        public XmlMessageEditor()
        {
        }

        /// <summary>
        /// Determine if this plugin supports the content type.
        /// </summary>
        /// <param name="contentType">The content type to test.</param>
        /// <returns>Returns true if the plugin supports the specified content type.</returns>
        public bool SupportsContentType(string contentType)
        {
            return contentType.ToLower().Contains("xml");
        }

        /// <summary>
        /// Create a UserControl to edit the specified bytes.
        /// This control will be hosted in the
        /// plugin dialog which provides OK and Cancel buttons.
        /// </summary>
        /// <param name="contentType">The content type of the BinaryHttpBody.</param>
        /// <param name="initialValue">The bytes to edit. The bytes are the payload of a BinaryHttpBody.</param>
        /// <returns>A UserControl capable of displaying and editing the byte array value of the specified content type.</returns>
        public object CreateEditor(string contentType, string initialValue)
        {
            messageEditorControl = new MessageEditorControl();
            messageEditorControl.EditString = initialValue;
            return this.messageEditorControl;
        }

        /// <summary>
        /// Gets the edited bytes after the OK button is clicked on the plugin dialog.
        /// </summary>
        public string GetNewValue()
        {
            return messageEditorControl.EditString;
        }

        private MessageEditorControl messageEditorControl;
    }
    ```

## <a name="add-a-ibinaryhttpbodyeditorplugin-to-the-class"></a>Sınıfa bir IBinaryHttpBodyEditorPlugin ekleyin

<xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin> arabirimini gerçekleştirin.

**Bu yordamdaki koda genel bakış**

Arabirim için kod uygulama, <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin> <xref:Microsoft.VisualStudio.TestTools.WebTesting.IStringHttpBodyEditorPlugin> önceki yordamda kapsanan öğesine benzerdir. Ancak, ikili sürüm dize yerine ikili verileri işlemek için bir bayt dizisi kullanır.

<xref:System.Windows.Forms.UserControl>İlk yordamda oluşturulan messageEditorControl MessageEditorControl olarak oluşturulur:

```csharp
private MessageEditorControl messageEditorControl
```

MessageEditorControl örneği, yöntemi tarafından oluşturulan eklenti iletişim kutusunda barındırılır <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin.CreateEditor*> . Ek olarak, messageEditorControl <xref:System.Windows.Forms.RichTextBox> , içindeki içeriğiyle doldurulur <xref:Microsoft.VisualStudio.TestTools.WebTesting.IHttpBody> . Ancak, döndürülmediği takdirde eklenti oluşturma gerçekleşemez <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin.SupportsContentType*> `true` . Bu düzenleyici söz konusu olduğunda, <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin.SupportsContentType*> `true` <xref:Microsoft.VisualStudio.TestTools.WebTesting.IHttpBody.ContentType*> içinde <xref:Microsoft.VisualStudio.TestTools.WebTesting.IHttpBody> "msbin1" varsa öğesini döndürür.

Dize gövdesinin düzenlenmesi tamamlandığında ve Kullanıcı eklenti iletişim kutusunda **Tamam** ' ı tıklattığında, <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin.GetNewValue*> düzenlenmiş metni bir dize olarak almak ve Web test performansı Düzenleyicisi 'Ndeki Istekteki **BinaryHttpBody. Data** öğesini güncelleştirmek için çağırılır.

### <a name="to-add-the-ibinaryhttpbodyeditorplugin-to-the-class"></a>Sınıfına IBinaryHttpBodyEditorPlugin eklemek için

- Arabiriminden Msbin1MessageEditor sınıfının örneğini oluşturmak <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin> ve gerekli yöntemleri uygulamak için önceki yordamda eklenen XmlMessageEditor sınıfının altına aşağıdaki kodu yazın veya kopyalayın:

    ```csharp
    /// <summary>
        /// Editor for MSBin1 content type (WCF messages)
        /// </summary>
        public class Msbin1MessageEditor : IBinaryHttpBodyEditorPlugin
        {
            /// <summary>
            ///
            /// </summary>
            public Msbin1MessageEditor()
            {
            }

            /// <summary>
            /// Determine if this plugin supports a content type.
            /// </summary>
            /// <param name="contentType">The content type to test.</param>
            /// <returns>Returns true if the plugin supports the specified content type.</returns>
            public bool SupportsContentType(string contentType)
            {
                return contentType.ToLower().Contains("msbin1");
            }

            /// <summary>
            /// Create a UserControl to edit the specified bytes. This control will be hosted in the
            /// plugin dialog which provides OK and Cancel buttons.
            /// </summary>
            /// <param name="contentType">The content type of the BinaryHttpBody.</param>
            /// <param name="initialValue">The bytes to edit. The bytes are the payload of a BinaryHttpBody.</param>
            /// <returns>A UserControl capable of displaying and editing the byte array value of the specified content type.</returns>
            public object CreateEditor(string contentType, byte[] initialValue)
            {
                messageEditorControl = new MessageEditorControl();
                messageEditorControl.EditByteArray = initialValue;
                return messageEditorControl;
            }

            /// <summary>
            /// Gets the edited bytes after the OK button is clicked on the plugin dialog.
            /// </summary>
            public byte[] GetNewValue()
            {
                return messageEditorControl.EditByteArray;
            }

            private MessageEditorControl messageEditorControl;
            private object originalMessage;
        }
    ```

## <a name="build-and-deploy-the-plug-ins"></a>Eklentileri derleme ve dağıtma

1. **Yapı** menüsünde, **Oluştur \<Windows Form Control Library project name>**' u seçin.

2. Visual Studio 'nun tüm örneklerini kapatın.

   > [!NOTE]
   > Visual Studio 'Yu kapatmak, kopyalamayı denemeden önce *. dll* dosyasının kilitlenmediğinden emin olmanızı sağlar.

3. Elde edilen *. dll* dosyasını projenizin *bin\Debug* klasöründen (örneğin, *MessageEditors.dll*) *%ProgramFiles%\Microsoft Visual studio\2017 \\ \<edition> \Common7\IDE\PrivateAssemblies\WebTestPlugins* dizinine kopyalayın.

4. Visual Studio'yu açın.

   *. Dll* artık Visual Studio ile kaydedilir.

## <a name="verify-the-plug-ins-using-a-web-performance-test"></a>Web performans testini kullanarak eklentileri doğrulama

1. Bir test projesi oluşturun.

2. Web performans testi oluşturun ve bir Web hizmetine tarayıcıda bir URL girin.

3. Kaydı tamamladığınızda, Web Performans Testi Düzenleyicisi Web hizmeti için isteği genişletin ve bir **dize gövdesi** ya da **ikili gövde** seçin.

4. **Özellikler** penceresinde, dize gövdesi veya ikili gövde ' yi seçin ve üç nokta **(...)** simgesini seçin.

   **Http gövde verilerini Düzenle** iletişim kutusu görüntülenir.

5. Artık verileri düzenleyebilir ve **Tamam**' ı seçebilirsiniz. Bu, içindeki içerikleri güncelleştirmek için uygulanabilir GetNewValue yöntemini çağırır <xref:Microsoft.VisualStudio.TestTools.WebTesting.IHttpBody> .

## <a name="compile-the-code"></a>Kodu derle

Windows Denetim Kitaplığı projesi için hedeflenen Framework 'ün .NET Framework 4,5 olduğunu doğrulayın. Varsayılan olarak, Windows denetim kitaplığı projeleri, Microsoft. VisualStudio. QualityTools. WebTestFramework başvurusunun eklenmesine izin vermeyecek .NET Framework 4,5 Istemci çerçevesini hedefleyin.

Daha fazla bilgi için bkz. [uygulama sayfası, proje Tasarımcısı (C#)](../ide/reference/application-page-project-designer-csharp.md).

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualStudio.TestTools.WebTesting.IStringHttpBodyEditorPlugin>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.IHttpBody>
- <xref:System.Windows.Forms.UserControl>
- <xref:System.Windows.Forms.RichTextBox>
- [Yük testleri için özel kod ve eklentiler oluşturma](../test/create-custom-code-and-plug-ins-for-load-tests.md)
- [Nasıl yapılır: istek düzeyi eklentisi oluşturma](../test/how-to-create-a-request-level-plug-in.md)
- [Web performans testi için özel bir ayıklama kuralı kodlayın](../test/code-a-custom-extraction-rule-for-a-web-performance-test.md)
- [Web performans testi için özel doğrulama kuralı kodu oluşturma](../test/code-a-custom-validation-rule-for-a-web-performance-test.md)
- [Nasıl yapılır: yük testi eklentisi oluşturma](../test/how-to-create-a-load-test-plug-in.md)
- [Kodlanmış web performans testi oluşturma](../test/generate-and-run-a-coded-web-performance-test.md)
- [Nasıl yapılır: Web performans Test Sonuçları Görüntüleyicisi için Visual Studio eklentisi oluşturma](../test/how-to-create-an-add-in-for-the-web-performance-test-results-viewer.md)
