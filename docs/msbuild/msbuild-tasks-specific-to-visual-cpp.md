---
title: MSBuild C++ görevlerine özgü | Microsoft Docs
description: C++ MSBuild C++ kodu oluşturmada kullanılan C++ MSBuild kullanılabilir görevlere bakın.
ms.custom: SEO-VS-2020
ms.date: 03/10/2019
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, tasks specific to C++
ms.assetid: 05410f0c-7356-4692-bc00-20664421c9ff
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- cplusplus
ms.openlocfilehash: 2a630842092f18d81257877742f872d3a01fe862
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122077146"
---
# <a name="msbuild-tasks-specific-to-c"></a>MSBuild C++ için özel görevler

Görevler, derleme işlemi sırasında çalışan kodu sağlar. C++ yüklendikten sonra, aşağıdaki görevler kullanılabilir ve bu görevler, MSBuild. Daha fazla bilgi için [bkz. MSBuild (C++) genel bakış.](/cpp/build/msbuild-visual-cpp-overview)

 Her görevin parametrelerine ek olarak, her görev de aşağıdaki parametrelere sahip olur.

| Parametre | Açıklama |
|-------------------| - |
| `Condition` | İsteğe `String` bağlı parametre.<br /><br /> MSBuild `Boolean` altyapısının bu görevin yürütülecek olup olmadığını belirlemek için kullandığı ifade. MSBuild tarafından desteklenen koşullar hakkında bilgi MSBuild [bkz. Koşullar.](../msbuild/msbuild-conditions.md) |
| `ContinueOnError` | İsteğe bağlı parametre. Aşağıdaki değerlerden birini içerebilir:<br /><br /> -   **WarnAndContinue veya** **true**. Bir görev başarısız olduğunda, [Target](../msbuild/target-element-msbuild.md) öğesinde ve derlemede sonraki görevler yürütülebilir ve görevdeki tüm hatalar uyarı olarak kabul edilir<br />-   **ErrorAndContinue**. Bir görev başarısız olduğunda, öğesinde ve derlemede sonraki görevler yürütülebilir ve görevdeki tüm `Target` hatalar hata olarak kabul edilir.<br />-   **ErrorAndStop** veya **false** (varsayılan). Bir görev başarısız olduğunda, öğesinde ve derlemede kalan görevler yürütülmez ve tüm öğe ile `Target` `Target` derlemenin başarısız olduğu kabul edilir.<br /><br /> 4.5'.NET Framework önceki sürümler yalnızca ve `true` değerlerini `false` destekler.<br /><br /> Daha fazla bilgi için, [bkz. How to: Ignore errors in tasks](../msbuild/how-to-ignore-errors-in-tasks.md). |

### <a name="related-topics"></a>İlgili konular

|Başlık|Açıklama|
|-----------|-----------------|
|[BscMake görevi](../msbuild/bscmake-task.md)|Microsoft Gözatma Bilgileri Bakım Yardımcı Programı aracını sarmalar (*bscmake.exe*).|
|[CL görevi](../msbuild/cl-task.md)|C++ derleyici aracını sarmalar (*cl.exe*).|
|[CPPClean görevi](../msbuild/cppclean-task.md)|Bir C++ projesi MSBuild oluşturduğu geçici dosyaları siler.|
|[ClangCompile görevi](../msbuild/clangcompile-task.md)|C++ derleyici aracını sarmalar (*clang.exe*).|
|[CustomBuild görevi](../msbuild/custombuild-task.md)|C++ derleyici aracını sarmalar (*cmd.exe*).|
|[FXC görevi](../msbuild/fxc-task.md)|Derleme sürecinde HLSL gölgelendirici derleyicilerini kullanın.|
|[GetOutOfDateItems](../msbuild/getoutofdateitems-task.md)|Eski tlog'ları okur, yeni tlog'lar yazar ve güncel olmayan öğe kümelerini döndürür. (yardımcı görev)|
|[GetOutputFileName](../msbuild/getoutputfilename-task.md)|Cl ve diğer araçlar için yalnızca çıkış dizini ya da tam dosya adı ya da hiçbir şey belirtmeye olanak sağlayan çıkış dosyası adını alır. (yardımcı görev)|
|[LIB görevi](../msbuild/lib-task.md)|Microsoft 32 Bit Kitaplık Yöneticisi aracını sarmalar (*lib.exe*).|
|[Bağlantı görevi](../msbuild/link-task.md)|C++ bağlama aracını sarmalar (*link.exe*).|
|[MIDL görevi](../msbuild/midl-task.md)|Microsoft Arabirim Tanımlama Dili (MIDL) derleyici aracını sarmalar (*midl.exe).*|
|[MT görevi](../msbuild/mt-task.md)|Microsoft Bildirim Aracı'nı sarmalar (*mt.exe*).|
|[MultiToolTask görevi](../msbuild/multitooltask-task.md)|Açıklama yok.|
|[ParallelCustomBuild görevi](../msbuild/parallelcustombuild-task.md)|CustomBuild görevinin [paralel örneklerini çalıştırın.](../msbuild/custombuild-task.md)|
|[RC görevi](../msbuild/rc-task.md)|Microsoft Windows Kaynak Derleyicisi aracını sarmalar (*rc.exe*).|
|[SetEnv görevi](../msbuild/setenv-task.md)|Belirtilen ortam değişkeninin değerini ayarlar veya siler.|
|[TrackedVCToolTask temel sınıfı](../msbuild/trackedvctooltask-base-class.md)|[VCToolTask'tan devralıyor.](../msbuild/vctooltask-base-class.md)|
|[VCMessage görevi](../msbuild/vcmessage-task.md)|Derleme sırasında uyarı iletilerini ve hata iletilerini günlüğe kaydeder. (Genişletilemez. Yalnızca dahili kullanım.)|
|[VCToolTask temel sınıfı](../msbuild/vctooltask-base-class.md)|[ToolTask'tan devralıyor.](/dotnet/api/microsoft.build.utilities.tooltask)|
|[XDCMake görevi](../msbuild/xdcmake-task.md)|XML belge açıklaması (*.xdc*)*dosyalarını* birxdcmake.exedosyası haline dönüştüren XML Belgeleri *aracını* (.xmlsarmalar.|
|[XSD görevi](../msbuild/xsd-task.md)|Bir kaynaktan şema veya sınıfxsd.exe *xml* şema tanımı aracını (xsd.exe) sarmalar. *Aşağıdaki nota bakın.*|
|[MSBuild başvurusu](../msbuild/msbuild-reference.md)|Bir sistem için MSBuild açıklar.|
|[Görevler](../msbuild/msbuild-tasks.md)|Derleme oluşturmak için birleştirilebilir kod birimleri olan görevleri açıklar.|
|[Görev yazma](../msbuild/task-writing.md)|Bir görevin nasıl oluşturulacağını açıklar.|

> [!NOTE]
> 2017'Visual Studio başlayarak,xsd.exeiçin C++ *proje* desteği kullanım dışıdır. GaC'ye el ile uygulama ekleyerek **Microsoft.VisualC.CppCodeProvider** *API'leriniCppCodeProvider.dll* kullanabilirsiniz.
