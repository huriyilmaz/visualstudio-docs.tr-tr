---
title: EditorConfig Için .NET kodlama kuralı ayarları
ms.date: 06/14/2018
ms.topic: reference
helpviewer_keywords:
- coding conventions [EditorConfig]
- EditorConfig coding conventions
- language code style rules [EditorConfig]
- formatting conventions [EditorConfig]
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 99d83157e2b6d108eb87a701aa8bc05ca2c7b1e6
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72653713"
---
# <a name="net-coding-convention-settings-for-editorconfig"></a>EditorConfig için .NET kodlama kuralı ayarları

Bir [Editorconfig](../ide/create-portable-custom-editor-options.md) dosyası kullanımıyla kod tabanınızda tutarlı kod stili tanımlayabilir ve bakımını yapabilirsiniz. EditorConfig, `indent_style` ve `indent_size` gibi birçok temel biçimlendirme özelliği içerir. Visual Studio 'da, .NET kodlama kuralları ayarları bir EditorConfig dosyası kullanılarak da yapılandırılabilir. Bireysel .NET kodlama kurallarını etkinleştirebilir veya devre dışı bırakabilir ve her kuralın uygulanmasını istediğiniz dereceyi bir önem düzeyi aracılığıyla yapılandırabilirsiniz.

> [!TIP]
> - Bir EditorConfig dosyasında kodlama kuralları tanımladığınızda, kodunuzu çözümlemek üzere Visual Studio 'da yerleşik olarak bulunan [kod stili Çözümleyicileri](../code-quality/roslyn-analyzers-overview.md) nasıl istediğinizi yapılandırıyorsunuz. EditorConfig dosyası, bu çözümleyiciler için yapılandırma dosyasıdır.
> - Visual Studio için kod stili tercihleri [metin düzenleyici seçenekleri](code-styles-and-code-cleanup.md) iletişim kutusunda da ayarlanabilir. Ancak, EditorConfig ayarları öncelik ve **Seçenekler** bölümünde ayarladığınız tercihleri belirli bir projeyle ilişkilendirilmemiş şekilde alır.

## <a name="convention-categories"></a>Kural kategorileri

Desteklenen üç .NET kodlama kuralı kategorisi vardır:

- [Dil kuralları](../ide/editorconfig-language-conventions.md)

   C# Veya Visual Basic diliyle ilgili kurallar. Örneğin, değişkenleri tanımlarken `var` veya açık türler veya ifade Bodied Üyeler tercih ediliyor gibi kuralları belirleyebilirsiniz.

- [Biçimlendirme kuralları](../ide/editorconfig-formatting-conventions.md)

   Daha kolay okunmasını sağlamak için kodunuzun düzeni ve yapısıyla ilgili kurallar. Örneğin, Allman küme ayraçları etrafında kuralları belirtebilir veya denetim bloklarındaki boşlukları tercih edebilirsiniz.

- [Adlandırma kuralları](../ide/editorconfig-naming-conventions.md)

   Kod öğelerinin adlandırılmasıyla ilgili kurallar. Örneğin, `async` yöntemlerinin "Async" ile bitmesi gerektiğini belirtebilirsiniz.

## <a name="example-editorconfig-file"></a>Örnek EditorConfig dosyası

Başlamanıza yardımcı olmak için, varsayılan seçeneklere sahip bir örnek *. editorconfig* dosyası aşağıda verilmiştir:

```ini
###############################
# Core EditorConfig Options   #
###############################

root = true

# All files
[*]
indent_style = space

# Code files
[*.{cs,csx,vb,vbx}]
indent_size = 4
insert_final_newline = true
charset = utf-8-bom

###############################
# .NET Coding Conventions     #
###############################

[*.{cs,vb}]
# Organize usings
dotnet_sort_system_directives_first = true
dotnet_separate_import_directive_groups = false

# this. preferences
dotnet_style_qualification_for_field = false:silent
dotnet_style_qualification_for_property = false:silent
dotnet_style_qualification_for_method = false:silent
dotnet_style_qualification_for_event = false:silent

# Language keywords vs BCL types preferences
dotnet_style_predefined_type_for_locals_parameters_members = true:silent
dotnet_style_predefined_type_for_member_access = true:silent

# Parentheses preferences
dotnet_style_parentheses_in_arithmetic_binary_operators = always_for_clarity:silent
dotnet_style_parentheses_in_relational_binary_operators = always_for_clarity:silent
dotnet_style_parentheses_in_other_binary_operators = always_for_clarity:silent
dotnet_style_parentheses_in_other_operators = never_if_unnecessary:silent

# Modifier preferences
dotnet_style_require_accessibility_modifiers = for_non_interface_members:silent
dotnet_style_readonly_field = true:suggestion

# Expression-level preferences
dotnet_style_object_initializer = true:suggestion
dotnet_style_collection_initializer = true:suggestion
dotnet_style_explicit_tuple_names = true:suggestion
dotnet_style_null_propagation = true:suggestion
dotnet_style_coalesce_expression = true:suggestion
dotnet_style_prefer_is_null_check_over_reference_equality_method = true:silent
dotnet_style_prefer_inferred_tuple_names = true:suggestion
dotnet_style_prefer_inferred_anonymous_type_member_names = true:suggestion
dotnet_style_prefer_auto_properties = true:silent
dotnet_style_prefer_conditional_expression_over_assignment = true:silent
dotnet_style_prefer_conditional_expression_over_return = true:silent

###############################
# Naming Conventions          #
###############################

# Style Definitions
dotnet_naming_style.pascal_case_style.capitalization             = pascal_case

# Use PascalCase for constant fields
dotnet_naming_rule.constant_fields_should_be_pascal_case.severity = suggestion
dotnet_naming_rule.constant_fields_should_be_pascal_case.symbols  = constant_fields
dotnet_naming_rule.constant_fields_should_be_pascal_case.style    = pascal_case_style
dotnet_naming_symbols.constant_fields.applicable_kinds            = field
dotnet_naming_symbols.constant_fields.applicable_accessibilities  = *
dotnet_naming_symbols.constant_fields.required_modifiers          = const

###############################
# C# Code Style Rules         #
###############################

[*.cs]
# var preferences
csharp_style_var_for_built_in_types = true:silent
csharp_style_var_when_type_is_apparent = true:silent
csharp_style_var_elsewhere = true:silent

# Expression-bodied members
csharp_style_expression_bodied_methods = false:silent
csharp_style_expression_bodied_constructors = false:silent
csharp_style_expression_bodied_operators = false:silent
csharp_style_expression_bodied_properties = true:silent
csharp_style_expression_bodied_indexers = true:silent
csharp_style_expression_bodied_accessors = true:silent

# Pattern-matching preferences
csharp_style_pattern_matching_over_is_with_cast_check = true:suggestion
csharp_style_pattern_matching_over_as_with_null_check = true:suggestion

# Null-checking preferences
csharp_style_throw_expression = true:suggestion
csharp_style_conditional_delegate_call = true:suggestion

# Modifier preferences
csharp_preferred_modifier_order = public,private,protected,internal,static,extern,new,virtual,abstract,sealed,override,readonly,unsafe,volatile,async:suggestion

# Expression-level preferences
csharp_prefer_braces = true:silent
csharp_style_deconstructed_variable_declaration = true:suggestion
csharp_prefer_simple_default_expression = true:suggestion
csharp_style_pattern_local_over_anonymous_function = true:suggestion
csharp_style_inlined_variable_declaration = true:suggestion

###############################
# C# Formatting Rules         #
###############################

# New line preferences
csharp_new_line_before_open_brace = all
csharp_new_line_before_else = true
csharp_new_line_before_catch = true
csharp_new_line_before_finally = true
csharp_new_line_before_members_in_object_initializers = true
csharp_new_line_before_members_in_anonymous_types = true
csharp_new_line_between_query_expression_clauses = true

# Indentation preferences
csharp_indent_case_contents = true
csharp_indent_switch_labels = true
csharp_indent_labels = flush_left

# Space preferences
csharp_space_after_cast = false
csharp_space_after_keywords_in_control_flow_statements = true
csharp_space_between_method_call_parameter_list_parentheses = false
csharp_space_between_method_declaration_parameter_list_parentheses = false
csharp_space_between_parentheses = false
csharp_space_before_colon_in_inheritance_clause = true
csharp_space_after_colon_in_inheritance_clause = true
csharp_space_around_binary_operators = before_and_after
csharp_space_between_method_declaration_empty_parameter_list_parentheses = false
csharp_space_between_method_call_name_and_opening_parenthesis = false
csharp_space_between_method_call_empty_parameter_list_parentheses = false
csharp_space_after_comma = true
csharp_space_after_dot = false

# Wrapping preferences
csharp_preserve_single_line_statements = true
csharp_preserve_single_line_blocks = true

##################################
# Visual Basic Code Style Rules  #
##################################

[*.vb]
# Modifier preferences
visual_basic_preferred_modifier_order = Partial,Default,Private,Protected,Public,Friend,NotOverridable,Overridable,MustOverride,Overloads,Overrides,MustInherit,NotInheritable,Static,Shared,Shadows,ReadOnly,WriteOnly,Dim,Const,WithEvents,Widening,Narrowing,Custom,Async:suggestion
```

## <a name="see-also"></a>Ayrıca bkz.

- [Hızlı Eylemler](../ide/quick-actions.md)
- [Taşınabilir özel düzenleyici seçenekleri oluştur](../ide/create-portable-custom-editor-options.md)
- [.NET Compiler Platform. editorconfig dosyası](https://github.com/dotnet/roslyn/blob/master/.editorconfig)