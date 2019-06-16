Names of Assemblies and DLLs
============================

An assembly is the unit of deployment and identity for managed code
programs. Although assemblies can span one or more files, typically an
assembly maps one-to-one with a DLL. Therefore, this section describes
only DLL naming conventions, which then can be mapped to assembly naming
conventions.

**✓ DO** choose names for your assembly DLLs that suggest large chunks
of functionality, such as System.Data.

Assembly and DLL names don’t have to correspond to namespace names, but
it is reasonable to follow the namespace name when naming assemblies. A
good rule of thumb is to name the DLL based on the common prefix of the
namespaces contained in the assembly. For example, an assembly with two
namespaces, ``MyCompany.MyTechnology.FirstFeature`` and
``MyCompany.MyTechnology.SecondFeature``, could be called
``MyCompany.MyTechnology.dll``.

**✓ CONSIDER** naming DLLs according to the following pattern:

``<Company>.<Component>.dll``

where ``<Component>`` contains one or more dot-separated clauses. For
example:

``Litware.Controls.dll``.
