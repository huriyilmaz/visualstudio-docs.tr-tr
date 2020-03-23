---
title: C++ Özel MSBuild Görevleri | Microsoft Dokümanlar
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
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 6393e771f9e9ed862d21397dabacdb3f3808c386
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633154"
---
# <a name="msbuild-tasks-specific-to-c"></a>C++'a özgü MSBuild görevleri

Görevler, yapı işlemi sırasında çalışan kodu sağlar. C++ yüklendiğinde, MSBuild yüklü görevlere ek olarak aşağıdaki görevler kullanılabilir. Daha fazla bilgi için [MSBuild (C++) genel bakış](/cpp/build/msbuild-visual-cpp-overview)bakın.

 Her görev için parametrelere ek olarak, her görev de aşağıdaki parametrelere sahiptir.

| Parametre | Açıklama |
|-------------------| - |
| `Condition` | İsteğe bağlı `String` parametre.<br /><br /> `Boolean` MSBuild altyapısının bu görevin yürütülüp yürütülmeyeceğini belirlemek için kullandığı ifade. MSBuild tarafından desteklenen koşullar hakkında bilgi için [Koşullar'a](../msbuild/msbuild-conditions.md)bakın. |
| `ContinueOnError` | İsteğe bağlı parametre. Aşağıdaki değerlerden birini içerebilir:<br /><br /> -   **WarnAndContinue** veya **doğru**. Bir görev başarısız olduğunda, [Hedef](../msbuild/target-element-msbuild.md) öğe ve yapıdaki sonraki görevler yürütmeye devam eder ve görevdeki tüm hatalar uyarı olarak kabul edilir<br />-   **HataandContinue**. Bir görev başarısız olduğunda, `Target` öğe ve yapı sonraki görevler yürütmeye devam eder ve görevden tüm hatalar hata olarak kabul edilir.<br />-   **ErrorAndStop** veya **false** (varsayılan). Bir görev başarısız olduğunda,`Target` öğe ve yapıda kalan görevler yürütülmez ve tüm `Target` öğe ve yapı başarısız olmuş olarak kabul edilir.<br /><br /> .NET Framework'ün 4.5'ten önceki `true` `false` sürümleri yalnızca değerleri ve değerleri desteklemişti.<br /><br /> Daha fazla bilgi için [bkz: Görevlerdeki hataları yoksay.](../msbuild/how-to-ignore-errors-in-tasks.md) |

### <a name="related-topics"></a>İlgili konular

|Başlık|Açıklama|
|-----------|-----------------|
|[BscGörev yap](../msbuild/bscmake-task.md)|Microsoft Gözatma Bilgi Bakım Programı aracını sarar (*bscmake.exe*).|
|[CL görevi](../msbuild/cl-task.md)|C++ derleyici aracını *(cl.exe)* sarar.|
|[CPPClean görevi](../msbuild/cppclean-task.md)|Bir C++ projesi oluşturulurken MSBuild'in oluşturduğu geçici dosyaları siler.|
|[ClangCompile görevi](../msbuild/clangcompile-task.md)|C++ derleyici aracını sarar (*clang.exe*).|
|[CustomBuild görevi](../msbuild/custombuild-task.md)|C++ derleyici aracını sarar (*cmd.exe*).|
|[FXC görevi](../msbuild/fxc-task.md)|Yapı işleminde HLSL shader derleyicilerini kullanın.|
|[GetOutOfDate Öğeler](../msbuild/getoutofdateitems-task.md)|Eski tlogları okur, yeni tloglar yazar ve güncel olmayan öğeler kümesini döndürür. (yardımcı görev)|
|[GetOutputFileName](../msbuild/getoutputfilename-task.md)|Cl ve yalnızca çıktı dizini veya tam dosya adı veya hiçbir şey belirtmeye izin veren diğer araçlar için çıktı dosya adı alır. (yardımcı görev)|
|[LIB görevi](../msbuild/lib-task.md)|Microsoft 32-Bit Kitaplık Yöneticisi aracını *(lib.exe)* sarar.|
|[Bağlantı görevi](../msbuild/link-task.md)|C++ bağlayıcı aracını sarar (*link.exe*).|
|[MIDL görevi](../msbuild/midl-task.md)|Microsoft Arabirim Tanımı Dili (MIDL) derleyici aracını *(midl.exe)* sarar.|
|[MT görevi](../msbuild/mt-task.md)|Microsoft Manifest Aracını *(mt.exe)* sarar.|
|[MultiToolTask görevi](../msbuild/multitooltask-task.md)|Tarifi yok.|
|[ParallelCustomBuild görevi](../msbuild/parallelcustombuild-task.md)|[CustomBuild görevinin](../msbuild/custombuild-task.md)paralel örneklerini çalıştırın.|
|[RC görevi](../msbuild/rc-task.md)|Microsoft Windows Kaynak Derleyici aracını sarar (*rc.exe*).|
|[SetEnv görev](../msbuild/setenv-task.md)|Belirli bir ortam değişkeninin değerini ayarlar veya siler.|
|[Paletli VCToolTask taban sınıfı](../msbuild/trackedvctooltask-base-class.md)|[VCToolTask'tan](../msbuild/vctooltask-base-class.md)devralır.|
|[VCMessage görevi](../msbuild/vcmessage-task.md)|Yapı sırasında uyarı iletilerini ve hata iletilerini günlüğe kaydeder. (Uzatılamaz. Yalnızca dahili kullanım.)|
|[VCToolTask taban sınıfı](../msbuild/vctooltask-base-class.md)|[ToolTask'tan](/dotnet/api/microsoft.build.utilities.tooltask)devralır.|
|[XDCMake görevi](../msbuild/xdcmake-task.md)|XML belge yorumunu (*.xdc*) dosyalarını bir *.xml* dosyasında birleştiren XML Dokümantasyon aracını *(xdcmake.exe)* sarar.|
|[XSD görevi](../msbuild/xsd-task.md)|Bir kaynaktan şema veya sınıf dosyaları üreten XML Şema Tanımı aracını *(xsd.exe)* sarar. *Aşağıdaki nota bakın.*|
|[MSBuild başvurusu](../msbuild/msbuild-reference.md)|MSBuild sisteminin öğelerini açıklar.|
|[Görevler](../msbuild/msbuild-tasks.md)|Bir yapı oluşturmak için birleştirilebilen kod birimleri olan görevleri açıklar.|
|[Görev yazma](../msbuild/task-writing.md)|Bir görevin nasıl oluşturulacağını açıklar.|

> [!NOTE]
> Visual Studio 2017'den itibaren *xsd.exe* için C++ proje desteği azalmaktadır. Gac'a *CppCodeProvider.dll'yi* el ile ekleyerek **Microsoft.VisualC.CppCodeProvider** API'lerini kullanmaya devam edebilirsiniz.
