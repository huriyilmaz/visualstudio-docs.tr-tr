---
title: 'İzlenecek yol: Çekirdek Düzenleyici oluşturma ve bir düzenleyici dosya türünü kaydetme | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - walkthrough
ms.assetid: 24d2bffd-a35c-46db-8515-fd60b884b7fb
caps.latest.revision: 30
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 14296aa335ba6710d4d9eac8e5338af7463c0aac
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65687644"
---
# <a name="walkthrough-creating-a-core-editor-and-registering-an-editor-file-type"></a>İzlenecek Yol: Temel Düzenleyici Oluşturma ve Düzenleyici Dosya Türü Kaydetme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu izlenecek yol [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ,. myext dosya adı uzantısına sahip bir dosya yüklendiğinde çekirdek düzenleyiciyi Başlatan bir VSPackage oluşturmayı gösterir.  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bu yönergeyi izlemek için, Visual Studio SDK 'sını yüklemelisiniz. Daha fazla bilgi için bkz. [Visual STUDIO SDK](../extensibility/visual-studio-sdk.md).  
  
## <a name="locations-for-the-visual-studio-package-project-template"></a>Visual Studio paketi proje şablonu konumları  
 Visual Studio paketi proje şablonu, **Yeni proje** iletişim kutusunda üç farklı konumda bulunabilir:  
  
1. Visual Basic genişletilebilirlik altında. Projenin varsayılan dili Visual Basic.  
  
2. C# genişletilebilirliği altında. Projenin varsayılan dili C# ' dir.  
  
3. Diğer proje türleri genişletilebilirliği altında. Projenin varsayılan dili C++ ' dır.  
  
### <a name="to-create-the-vspackage"></a>VSPackage oluşturmak için  
  
- [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]' İ başlatın ve [!INCLUDE[csprcs](../includes/csprcs-md.md)] `MyPackage` [Izlenecek yol: bir menü komutu olan VSPackage](https://msdn.microsoft.com/d699c149-5d1e-47ff-94c7-e1222af02c32)adlı bir VSPackage oluşturun.  
  
### <a name="to-add-the-editor-factory"></a>Düzenleyici fabrikası eklemek için  
  
1. **MyPackage** projesine sağ tıklayın, **Ekle** ' nin üzerine gelin ve ardından **sınıf**' a tıklayın.  
  
2. **Yeni öğe Ekle** iletişim kutusunda, **sınıf** şablonunun seçili olduğundan emin olun, `EditorFactory.cs` ad için yazın ve ardından **Ekle** ' ye tıklayarak sınıfı projenize ekleyin.  
  
     EditorFactory.cs dosyası otomatik olarak açılmalıdır.  
  
3. Kodunuzda aşağıdaki derlemelere başvuru yapın.  
  
    ```vb  
    Imports System.Runtime.InteropServices  
    Imports Microsoft.VisualStudio  
    Imports Microsoft.VisualStudio.Shell  
    Imports Microsoft.VisualStudio.Shell.Interop  
    Imports Microsoft.VisualStudio.OLE.Interop  
    Imports Microsoft.VisualStudio.TextManager.Interop  
    Imports IOleServiceProvider = Microsoft.VisualStudio.OLE.Interop.IServiceProvider  
    ```  
  
    ```csharp  
    using System.Runtime.InteropServices;  
    using Microsoft.VisualStudio;  
    using Microsoft.VisualStudio.Shell;  
    using Microsoft.VisualStudio.Shell.Interop;  
    using Microsoft.VisualStudio.OLE.Interop;  
    using Microsoft.VisualStudio.TextManager.Interop;  
    using IOleServiceProvider = Microsoft.VisualStudio.OLE.Interop.IServiceProvider;  
  
    ```  
  
4. `EditorFactory` `Guid` Sınıf bildiriminden hemen önce özniteliğini ekleyerek SıNıFA bir GUID ekleyin.  
  
     Komut isteminde guidgen.exe programını kullanarak [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] veya **Araçlar** menüsünde **GUID oluştur** ' a tıklayarak yeni bir GUID oluşturabilirsiniz. Burada kullanılan GUID yalnızca bir örnektir; Bunu projenizde kullanmayın.  
  
    ```vb  
    <Guid("0eea3187-c5fa-48d4-aa72-b5eecd3b17b1")> _  
    ```  
  
    ```csharp  
    [Guid("0eea3187-c5fa-48d4-aa72-b5eecd3b17b1")]   
    ```  
  
5. Sınıf tanımında, ana paketi ve bir hizmet sağlayıcısını içerecek şekilde iki özel değişken ekleyin.  
  
    ```vb  
    Class EditorFactory  
        Private parentPackage As Package  
        Private serviceProvider As IOleServiceProvider  
    ```  
  
    ```csharp  
    class EditorFactory  
    {  
        private Package parentPackage;  
        private IOleServiceProvider serviceProvider;  
    }  
  
    ```  
  
6. Türünde bir parametre alan bir ortak sınıf oluşturucu ekleyin <xref:Microsoft.VisualStudio.Shell.Package> :  
  
    ```vb  
    Public Sub New(ByVal parentPackage As Package)  
        Me.parentPackage = parentPackage  
    End Sub  
    ```  
  
    ```csharp  
    public EditorFactory(Package parentPackage)  
    {  
        this.parentPackage = parentPackage;  
    }  
    ```  
  
7. `EditorFactory`Arabirimden türetmek için sınıf bildirimini değiştirin <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> .  
  
    ```vb  
    Class EditorFactory Implements IVsEditorFacto  
    ```  
  
    ```csharp  
    class EditorFactory : IVsEditorFactory  
  
    ```  
  
8. Sağ tıklayın <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> , **arabirimi Uygula**' ya ve ardından **arabirimi açıkça Uygula**' ya tıklayın.  
  
     Bu, arayüzde uygulanması gereken dört yöntemi ekler <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> .  
  
9. `IVsEditorFactory.Close` yönteminin içeriğini aşağıdaki kodla değiştirin.  
  
    ```vb  
    Return VSConstants.S_OK  
    ```  
  
    ```csharp  
    return VSConstants.S_OK;  
    ```  
  
10. Öğesinin içeriğini `IVsEditorFactory.SetSite` aşağıdaki kodla değiştirin.  
  
    ```vb  
    Me.serviceProvider = psp  
    Return VSConstants.S_OK  
    ```  
  
    ```csharp  
    this.serviceProvider = psp;  
    return VSConstants.S_OK;  
    ```  
  
11. `IVsEditorFactory.MapLogicalView` yönteminin içeriğini aşağıdaki kodla değiştirin.  
  
    ```vb  
    Dim retval As Integer = VSConstants.E_NOTIMPL  
    pbstrPhysicalView = Nothing ' We support only one view.  
    If rguidLogicalView.Equals(VSConstants.LOGVIEWID_Designer)OrElse _  
    rguidLogicalView.Equals(VSConstants.LOGVIEWID_Primary) Then  
        retval = VSConstants.S_OK  
    End If  
    Return retval  
    ```  
  
    ```csharp  
    int retval = VSConstants.E_NOTIMPL;  
    pbstrPhysicalView = null;   // We support only one view.  
    if (rguidLogicalView.Equals(VSConstants.LOGVIEWID_Designer) ||  
    rguidLogicalView.Equals(VSConstants.LOGVIEWID_Primary))  
    {  
        retval = VSConstants.S_OK;  
    }  
    return retval;  
    ```  
  
12. `IVsEditorFactory.CreateEditorInstance` yönteminin içeriğini aşağıdaki kodla değiştirin.  
  
    ```vb  
    Dim retval As Integer = VSConstants.E_FAIL          
  
    ' Initialize these to empty to start with   
    ppunkDocView = IntPtr.Zero  
    ppunkDocData = IntPtr.Zero  
    pbstrEditorCaption = ""  
    pguidCmdUI = Guid.Empty  
    pgrfCDW = 0  
  
    If (grfCreateDoc And (VSConstants.CEF_OPENFILE Or _  
    VSConstants.CEF_SILENT)) = 0 Then  
        Throw New ArgumentException("Only Open or Silent is valid")  
    End If  
    If punkDocDataExisting <> IntPtr.Zero Then  
        Return VSConstants.VS_E_INCOMPATIBLEDOCDATA  
    End If  
  
    ' Instantiate a text buffer of type VsTextBuffer.   
    ' Note: we only need an IUnknown (object) interface for   
    ' this invocation.   
    Dim clsidTextBuffer As Guid = GetType(VsTextBufferClass).GUID  
    Dim iidTextBuffer As Guid = VSConstants.IID_IUnknown  
    Dim pTextBuffer As Object = pTextBuffer = _  
    parentPackage.CreateInstance(clsidTextBuffer, iidTextBuffer, _  
    GetType(Object))  
  
    If Not pTextBuffer Is Nothing Then  
        ' "Site" the text buffer with the service provider we were   
        ' provided.   
        Dim textBufferSite As IObjectWithSite = TryCast(pTextBuffer, _  
        IObjectWithSite)  
        If Not textBufferSite Is Nothing Then  
            textBufferSite.SetSite(Me.serviceProvider)  
        End If  
  
        ' Instantiate a code window of type IVsCodeWindow.   
        Dim clsidCodeWindow As Guid = GetType(VsCodeWindowClass).GUID  
        Dim iidCodeWindow As Guid = GetType(IVsCodeWindow).GUID  
        Dim pCodeWindow As IVsCodeWindow = _  
        CType(Me.parentPackage.CreateInstance(clsidCodeWindow, _  
        iidCodeWindow, GetType(IVsCodeWindow)), IVsCodeWindow)  
        If Not pCodeWindow Is Nothing Then  
            ' Give the text buffer to the code window.   
            ' We are giving up ownership of the text buffer!   
            pCodeWindow.SetBuffer(CType(pTextBuffer, IVsTextLines))  
  
            ' Now tell the caller about all this new stuff   
            ' that has been created.   
            ppunkDocView = Marshal.GetIUnknownForObject(pCodeWindow)  
            ppunkDocData = Marshal.GetIUnknownForObject(pTextBuffer)  
  
            ' Specify the command UI to use so keypresses are   
            ' automatically dealt with.   
            pguidCmdUI = VSConstants.GUID_TextEditorFactory  
  
            ' This caption is appended to the filename and   
            ' lets us know our invocation of the core editor   
            ' is up and running.   
            pbstrEditorCaption = " [MyPackage]"  
  
            retval = VSConstants.S_OK  
        End If  
    End If  
    Return retval  
    ```  
  
    ```csharp  
    int retval = VSConstants.E_FAIL;  
  
    // Initialize these to empty to start with  
    ppunkDocView       = IntPtr.Zero;  
    ppunkDocData       = IntPtr.Zero;  
    pbstrEditorCaption = "";  
    pguidCmdUI         = Guid.Empty;   
    pgrfCDW            = 0;  
  
    if ((grfCreateDoc & (VSConstants.CEF_OPENFILE |   
          VSConstants.CEF_SILENT)) == 0)  
    {   
        throw new ArgumentException("Only Open or Silent is valid");  
    }  
    if (punkDocDataExisting != IntPtr.Zero)  
    {  
        return VSConstants.VS_E_INCOMPATIBLEDOCDATA;  
    }  
  
    // Instantiate a text buffer of type VsTextBuffer.  
    // Note: we only need an IUnknown (object) interface for   
    // this invocation.  
    Guid clsidTextBuffer = typeof(VsTextBufferClass).GUID;  
    Guid iidTextBuffer   = VSConstants.IID_IUnknown;  
    object pTextBuffer   = pTextBuffer = parentPackage.CreateInstance(  
          ref clsidTextBuffer,  
          ref iidTextBuffer,  
          typeof(object));  
  
    if (pTextBuffer != null)  
    {  
        // "Site" the text buffer with the service provider we were  
        // provided.  
        IObjectWithSite textBufferSite = pTextBuffer as IObjectWithSite;  
        if (textBufferSite != null)  
        {  
            textBufferSite.SetSite(this.serviceProvider);  
        }  
  
        // Instantiate a code window of type IVsCodeWindow.  
        Guid clsidCodeWindow = typeof(VsCodeWindowClass).GUID;  
        Guid iidCodeWindow   = typeof(IVsCodeWindow).GUID;  
        IVsCodeWindow pCodeWindow =  
        (IVsCodeWindow)this.parentPackage.CreateInstance(   
              ref clsidCodeWindow,  
              ref iidCodeWindow,  
              typeof(IVsCodeWindow));  
        if (pCodeWindow != null)  
        {  
            // Give the text buffer to the code window.  
            // We are giving up ownership of the text buffer!  
            pCodeWindow.SetBuffer((IVsTextLines)pTextBuffer);  
  
            // Now tell the caller about all this new stuff   
            // that has been created.  
            ppunkDocView = Marshal.GetIUnknownForObject(pCodeWindow);  
            ppunkDocData = Marshal.GetIUnknownForObject(pTextBuffer);  
  
            // Specify the command UI to use so keypresses are   
            // automatically dealt with.  
            pguidCmdUI = VSConstants.GUID_TextEditorFactory;  
  
            // This caption is appended to the filename and  
            // lets us know our invocation of the core editor   
            // is up and running.  
            pbstrEditorCaption = " [MyPackage]";  
  
            retval = VSConstants.S_OK;  
        }   
    }   
    return retval;   
    ```  
  
13. Projeyi derleyin ve hata olmadığından emin olun.  
  
### <a name="to-register-the-editor-factory"></a>Düzenleyici fabrikasını kaydetmek için  
  
1. **Çözüm Gezgini**' de, Resources. resx dosyasına çift tıklayarak girdiyi **Dize1** Selected dize tablosunda açın.  
  
2. Tanımlayıcının adını `IDS_EDITORNAME` ve metnini **MyPackage Düzenleyicisi** olarak değiştirin. Bu dize, düzenleyicinin adı olarak görünür.  
  
3. VSPackage. resx dosyasını açın ve yeni bir dize ekleyin, adı **101** ve değerini olarak ayarlayın `IDS_EDITORNAME` . Bu, yeni oluşturduğunuz dizeye erişmek için bir kaynak KIMLIĞINE sahip paketi sağlar.  
  
    > [!NOTE]
    > VSPackage. resx dosyası, `name` özniteliğin **101**olarak ayarlandığı başka bir dize içeriyorsa, başka bir benzersiz, sayısal değer ve aşağıdaki adımlarda bu değeri değiştirin.  
  
4. **Çözüm Gezgini**, MyPackagePackage.cs dosyasını açın.  
  
     Bu, ana paket dosyasıdır.  
  
5. Aşağıdaki kullanıcı özniteliklerini özniteliğiyle hemen önce ekleyin `Guid` .  
  
    ```vb  
    <ProvideEditorFactoryAttribute(GetType(EditorFactory), 101)> _  
    <ProvideEditorExtensionAttribute(GetType(EditorFactory), _  
          ".myext", 32, NameResourceID:=101 )> _  
    ```  
  
    ```csharp  
    [ProvideEditorFactory(typeof(EditorFactory), 101)]  
    [ProvideEditorExtension(typeof(EditorFactory),   
          ".myext", 32, NameResourceID = 101)]   
    ```  
  
     <xref:Microsoft.VisualStudio.Shell.ProvideEditorExtensionAttribute>Özniteliği. myext dosya uzantısını düzenleyici fabrikasında ilişkilendirir, bu sayede bu uzantıya sahip bir dosya yüklendiğinde düzenleyici fabrikası çağırılır.  
  
6. Bir özel değişkeni `MyPackage` , oluşturucudan hemen önce sınıfa ekleyin ve türü verin `EditorFactory` .  
  
    ```vb  
    Private editorFactory As EditorFactory  
    ```  
  
    ```csharp  
    private EditorFactory editorFactory;  
    ```  
  
7. Yöntemini bulun `Initialize` ( `Package Members` gizli bölgeyi açmanız gerekebilir) ve çağrısından sonra aşağıdaki kodu ekleyin `base.Initialize()` .  
  
    ```vb  
    'Create our editor factory and register it.   
    Me.editorFactory = New EditorFactory(Me)  
    MyBase.RegisterEditorFactory(Me.editorFactory)  
    ```  
  
    ```csharp  
    // Create our editor factory and register it.  
    this.editorFactory = new EditorFactory(this);  
    base.RegisterEditorFactory(this.editorFactory);  
  
    ```  
  
8. Programı derleyin ve hata olmadığından emin olun.  
  
     Bu adım, düzenleyici fabrikasını için deneysel kayıt defteri kovanına kaydeder [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Resource. h dosyasını geçersiz kılmanız istenirse, **Tamam**' a tıklayın.  
  
9. TextFile1. myext adlı örnek bir dosya oluşturun.  
  
10. Deneysel bir örneğini açmak için **F5** tuşuna basın [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .  
  
11. Deneysel öğesinde [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] **Dosya** menüsünde **Aç** ' ın üzerine gelin ve ardından **Dosya**' ya tıklayın.  
  
12. TextFile1. myext bulun ve **Aç**' a tıklayın.  
  
     Dosya şimdi yüklenmelidir.  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]Çekirdek Düzenleyici, çok çeşitli metin tabanlı dosya türlerini işler ve sözdizimi vurgulama, küme ayracı eşleştirme ve IntelliSense sözcük tamamlama ve üye Tamamlama listeleri gibi zengin bir özellik kümesi sağlamak için dil hizmetleriyle yakın bir şekilde çalışmaktadır. Metin tabanlı dosyalarla çalışıyorsanız, temel düzenleyiciyi, belirli dosya türlerinizi destekleyen özel bir dil hizmetiyle birlikte kullanabilirsiniz.  
  
 Bir VSPackage, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] bir düzenleyici fabrikası sağlayarak çekirdek düzenleyiciyi çağırabilir. Bu düzenleyici fabrikası, onunla ilişkili bir dosya yüklendiğinde kullanılır. Dosya bir projenin parçasıysa, VSPackage tarafından geçersiz kılınmadıkça çekirdek Düzenleyici otomatik olarak çağrılır. Ancak, dosya bir projenin dışına yüklenirse, çekirdek Düzenleyici, VSPackage tarafından açıkça çağrılmalıdır.  
  
 Çekirdek Düzenleyici hakkında daha fazla bilgi için bkz. [Çekirdek Düzenleyici içindeki](../extensibility/inside-the-core-editor.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Çekirdek düzenleyicinin içinde](../extensibility/inside-the-core-editor.md)   
 [Eski API'yi Kullanarak Temel Düzenleyiciyi Başlatma](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md)
