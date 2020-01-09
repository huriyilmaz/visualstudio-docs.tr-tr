---
title: '| Öğesine C++ özgü MSBuild görevleri Microsoft Docs'
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
ms.openlocfilehash: 89f7d8465b2078d4c0c1ce86894edb834581596d
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75593830"
---
# <a name="msbuild-tasks-specific-to-c"></a>Öğesine özgü MSBuild görevleriC++
Görevler, derleme işlemi sırasında çalışan kodu sağlar. C++ Yüklendiğinde, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]ile yüklenenlere ek olarak aşağıdaki görevler kullanılabilir. Daha fazla bilgi için bkz. [MSBuildC++() genel bakış](/cpp/build/msbuild-visual-cpp-overview).

 Her görevin parametrelerine ek olarak, her görevin aşağıdaki parametreleri de vardır.

| Parametre | Açıklama |
|-------------------| - |
| `Condition` | İsteğe bağlı `String` parametresi.<br /><br /> [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] altyapısının bu görevin yürütülüp yürütülmeyeceğini belirlemede kullandığı `Boolean` ifadesi. [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]tarafından desteklenen koşullar hakkında daha fazla bilgi için bkz. [koşullar](../msbuild/msbuild-conditions.md). |
| `ContinueOnError` | İsteğe bağlı parametre. , Aşağıdaki değerlerden birini içerebilir:<br /><br /> -   **WarnAndContinue** ya da **true**. Bir görev başarısız olduğunda, [hedef](../msbuild/target-element-msbuild.md) öğe ve yapı içindeki sonraki görevler yürütülmeye devam eder ve görevdeki tüm hatalar uyarı olarak kabul edilir<br />-   **Errportadcontinue**. Bir görev başarısız olduğunda, `Target` öğesi ve derleme içindeki sonraki görevler yürütülmeye devam eder ve görevdeki tüm hatalar hata olarak değerlendirilir.<br />-   **Errportadstop** veya **false** (varsayılan). Bir görev başarısız olduğunda,`Target` öğesi ve derleme içindeki kalan görevler yürütülmez ve tüm `Target` öğesi ve derleme başarısız olduğu kabul edilir.<br /><br /> 4,5 öncesindeki .NET Framework sürümleri yalnızca `true` ve `false` değerlerini destekliyordu.<br /><br /> Daha fazla bilgi için bkz. [nasıl yapılır: görevlerdeki hataları yoksayma](../msbuild/how-to-ignore-errors-in-tasks.md). |

### <a name="related-topics"></a>İlgili konular

|Başlık|Açıklama|
|-----------|-----------------|
|[BscMake görevi](../msbuild/bscmake-task.md)|Microsoft tarayıcı bilgi Bakımı yardımcı programı aracını (*bscmake. exe*) sarar.|
|[CL görevi](../msbuild/cl-task.md)|C++ Derleyici aracını sarmalanmış (*CL. exe*).|
|[CPPClean görevi](../msbuild/cppclean-task.md)|Bir C++ proje oluşturulduğunda MSBuild tarafından oluşturulan geçici dosyaları siler.|
|[ClangCompile görevi](../msbuild/clangcompile-task.md)|C++ Derleyici aracını (*Clang. exe*) sarmalanmış.|
|[CustomBuild görevi](../msbuild/custombuild-task.md)|C++ Derleyici aracını sarmalanmış (*cmd. exe*).|
|[FXC görevi](../msbuild/fxc-task.md)|Yapı sürecinde HLSL gölgelendirici derleyicileri kullanın.|
|[GetOutOfDateItems](../msbuild/getoutofdateitems-task.md)|Eski tlogs dosyalarını okur, yeni tlogs yazar ve güncel olmayan öğe kümesi döndürür. (yardımcı görev)|
|[GetOutputFileName](../msbuild/getoutputfilename-task.md)|Yalnızca çıkış dizini veya tam dosya adı ya da hiçbir şey belirtilmesine izin veren CL ve diğer araçların çıkış dosyası adını alır. (yardımcı görev)|
|[LıB görevi](../msbuild/lib-task.md)|Microsoft 32-bit kitaplık Yöneticisi aracını (*lib. exe*) sarmalanmış.|
|[Bağlantı görevi](../msbuild/link-task.md)|C++ Bağlayıcı aracını sarmalanmış (*LINK. exe*).|
|[MıDL görevi](../msbuild/midl-task.md)|Microsoft Arabirim Tanımlama Dili (MıDL) derleyici aracını (*MIDL. exe*) kaydırır.|
|[MT görevi](../msbuild/mt-task.md)|Microsoft bildirim aracı 'nı (*mt. exe*) kaydırır.|
|[MultiToolTask görevi](../msbuild/multitooltask-task.md)|Açıklama yok.|
|[ParallelCustomBuild görevi](../msbuild/parallelcustombuild-task.md)|[CustomBuild görevinin](../msbuild/custombuild-task.md)paralel örneklerini çalıştırın.|
|[RC görevi](../msbuild/rc-task.md)|Microsoft Windows Kaynak derleyicisi aracı 'nı (*rc. exe*) kaydırır.|
|[SetEnv Görevi](../msbuild/setenv-task.md)|Belirtilen ortam değişkeninin değerini ayarlar veya siler.|
|[TrackedVCToolTask temel sınıfı](../msbuild/trackedvctooltask-base-class.md)|[Vctooltask](../msbuild/vctooltask-base-class.md)'dan devralır.|
|[VCMessage görevi](../msbuild/vcmessage-task.md)|Bir derleme sırasında uyarı iletilerini ve hata iletilerini günlüğe kaydeder. (Genişletilebilir değil. Yalnızca iç kullanım.)|
|[VCToolTask temel sınıfı](../msbuild/vctooltask-base-class.md)|[ToolTask](/dotnet/api/microsoft.build.utilities.tooltask)'dan devralır.|
|[XDCMake görevi](../msbuild/xdcmake-task.md)|XML belge açıklaması ( *. xdc*) dosyalarını bir *. XML* dosyasında birleştiren XML belge aracı 'nı (*xdcmake. exe*) kaydırır.|
|[XSD görevi](../msbuild/xsd-task.md)|Bir kaynaktan şema veya sınıf dosyaları üreten XML şema tanımı aracı 'nı (*XSD. exe*) sarmalanmış olarak kaydırır. *Aşağıdaki nota bakın.*|
|[MSBuild başvurusu](../msbuild/msbuild-reference.md)|MSBuild sisteminin öğelerini açıklar.|
|[Görevler](../msbuild/msbuild-tasks.md)|Bir yapı oluşturmak için birleştirilebilecek kod birimleri olan görevleri açıklar.|
|[Görev yazma](../msbuild/task-writing.md)|Bir görevin nasıl oluşturulacağını açıklar.|

> [!NOTE]
> Visual Studio 2017 ' den başlayarak C++ , *XSD. exe* için proje desteği kullanım dışıdır. *Cppcodeprovider. dll dosyasını* el ile GAC 'ye ekleyerek **Microsoft. VisualC. cppcodeprovider** API 'lerini kullanmaya devam edebilirsiniz.
