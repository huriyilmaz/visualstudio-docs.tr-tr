---
title: Dış araçları yönetme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.externaltools
helpviewer_keywords:
- Create GUID tool
- RC (Resource Compiler)
- ReBase tool
- Windows NT Message Compiler
- Windows NT C++ Symbol Undecorator
- tstcon32.exe
- Type Library Generator
- Windows NT Image Binder
- tools [Visual Studio], external
- RowsetViewer tool
- utilities, external tools
- Local Test Manager
- OLE DB Rowset Viewer
- Midlc (IDL Compiler)
- ATL Trace Tool
- Odbcte32w.exe
- IDL Compiler
- HCW (Help Workshop)
- Message Compiler [Visual Studio]
- UUID Generator
- MIDL, external tools
- ErrLook tool
- MAKEHM tool
- Error lookup tool
- OLEVIEW (Object Viewer)
- Uuidgen.exe
- WebDbg tool
- OLE/COM Object Viewer
- LTM (Local Test Manager)
- ATLTraceTool.exe
- Bind tool
- Vsvars32.bat
- external tools [Visual Studio]
- ODBC Test
- Windows NT Image Rebaser
- undname.exe
- Vcspawn.exe
- ActiveX Control Test Container
- mc (Message Compiler)
- GUIDGEN tool
- Odbcte32.exe
- DisableMsg tool
- MkTypLib tool
- Help Workshop
- Resource Compiler
ms.assetid: f382fd40-a98f-4934-8c9a-5aeae881acde
caps.latest.revision: 41
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7a9ebda81f013f42aeac23c9c0a8cc5a0a41f5f0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72651346"
---
# <a name="managing-external-tools"></a>Dış Araçları Yönetme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio 'Nun içinden dış araçlar çağırabilirsiniz. **Araçlar** menüsünde birkaç varsayılan araç mevcuttur, ancak kendi diğer yürütülebilir dosyalarını ekleyebilirsiniz.

## <a name="tools-available-on-the-visual-studio-tools-menu"></a>Visual Studio Araçları menüsünde bulunan araçlar
 İçindeki **Araçlar** menüsünden aşağıdaki araçları çağırabilirsiniz [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Ayrıca, bunları **Hızlı başlatma** penceresinden adına göre de çağırabilirsiniz. Örneğin, GuidGen.exe çağırmak için **GUID oluştur**yazın.

1. GUID oluştur: bir GUID oluşturur.

2. Hata arama: girilen değerden bir hata iletisi alır. Daha fazla bilgi için bkz. [ERRLOOK başvurusu](https://msdn.microsoft.com/library/6040ffc1-2355-4a45-8998-84cbcba4ca91).

3. ATL/MFC Izleme aracı: ATL ve MFC kaynaklarında hata ayıklama izleme iletilerini gösterir.

4. PreEmptive Protection-Dotfuscator: .NET programlarını tersine mühendisliğe karşı korur.

5. SPY + +: işlem, iş parçacıkları, pencereler ve pencere iletilerini grafiksel olarak görüntüler.

6. WCF hizmeti yapılandırma Düzenleyicisi: WCF Hizmetleri için yapılandırma ayarları oluşturmanıza ve değiştirmenize Izin verir.

> [!WARNING]
> Yüklediğiniz Visual Studio sürümüne ve uygulanan ayarlar profiline bağlı olarak, dış araçların farklı bir listesini görebilirsiniz. Daha fazla bilgi için bkz. [Visual Studio 'Da geliştirme ayarlarını özelleştirme](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

## <a name="adding-new-tools"></a>Yeni araçlar ekleme
 **Araçlar** menüsüne bir dış araç ekleyebilirsiniz. **Dış araçlar** iletişim kutusunu açın ve **Ekle**' ye tıklayın ve ardından bilgileri girin. Örneğin, aşağıdaki giriş, Windows Gezgini 'nin şu anda Visual Studio 'da açtığınız dosyanın dizininde açılmasını sağlar:

1. Başlık: dosya konumunu aç

2. Komut: explorer.exe

3. Bağımsız değişkenler:/root, "$ (ıtemdır)"

## <a name="arguments-for-external-tools"></a>Dış araçlar için bağımsız değişkenler
 Aşağıdaki bağımsız değişkenler, dış bir araç başlattığınızda atanan Visual Studio değişkenleridir. Not defteri veya Spy + + gibi dış araçların bağlantıları, Dış Araçlar iletişim kutusu kullanılarak **Araçlar** menüsünde listelenebilir.

> [!NOTE]
> IDE durum çubuğu, ekleme noktasının etkin kod düzenleyicisinde nerede olduğunu göstermek için geçerli satırı ve geçerli sütun değişkenlerini görüntüler. Geçerli metin değişkeni, bu konumda seçili olan metni veya kodu döndürür.

|Name|Bağımsız Değişken|Açıklama|
|----------|--------------|-----------------|
|Öğe yolu|$ (ItemPath)|Geçerli dosyanın (sürücü + yol + dosya adı) tüm dosya adı.|
|Öğe dizini|$ (Itemdır)|Geçerli dosyanın dizini (sürücü + yol).|
|Öğe dosyası adı|$ (Itemfilename)|Geçerli dosyanın (dosya adı) dosya adı.|
|Öğe uzantısı|$ (ItemExt)|Geçerli dosyanın dosya adı uzantısı.|
|Geçerli satır|$ (CurLine)|İmlecin kod penceresindeki geçerli satır konumu.|
|Geçerli sütun|$ (CurCol)|İmlecin kod penceresindeki geçerli sütun konumu.|
|Geçerli metin|$ (CurText)|Seçilen metin.|
|Hedef yol|$ (TargetPath)|Oluşturulacak öğenin tamamı dosya adı (sürücü + yol + dosya adı).|
|Hedef Dizin|$ (TARGETDIR)|Oluşturulacak öğenin dizini.|
|Hedef Adı|$ (TargetName)|Oluşturulacak öğenin dosya adı.|
|Hedef uzantısı|$ (TargetExt)|Oluşturulacak öğenin dosya adı uzantısı.|
|İkili dizin|$ (BinDir)|Oluşturulmakta olan ikilinin son konumu (sürücü + yol olarak tanımlanır). Örneğin:** \\ . ..\Bir Studio \<Version> \\<ProjectName \> \Bin\Debug**|
|Proje dizini|$ (ProjDir)|Geçerli projenin dizini (sürücü + yol).|
|Proje dosyası adı|$ (ProjFileName)|Geçerli projenin dosya adı (sürücü + yol + dosya adı).|
|Çözüm dizini|$ (SolutionDir)|Geçerli çözümün dizini (sürücü + yol).|
|Çözüm dosyası adı|$ (SolutionFileName)|Geçerli çözümün dosya adı (sürücü + yol + dosya adı).|

## <a name="see-also"></a>Ayrıca Bkz.
 [C/C++ Derleme Araçları](https://msdn.microsoft.com/library/48d9daf4-6bbf-473a-8ce2-bf2923b69f80)
