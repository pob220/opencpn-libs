# Provisional HostApi123 chart-safety header

This snapshot matches the coordinated API 1.23 core candidate. Published
HostApi122 declarations are unchanged. Chart operations are accessed through
GetHostApi() and a checked dynamic_cast<HostApi123*>.

This is a development interface, not a published plugin API level. API_VERSION
remains 1.22, the plugin load floor: HostApi123 inherits the released HostApi122
with out-of-line virtual functions and therefore depends on its RTTI. A plugin
built with this header cannot promise to load on hosts older than API 1.22.
Stock 5.14.2 loads such plugins; the cast must fail cleanly and chart operations
must be disabled. The new core returns a private concrete HostApi123 backend.

The Windows import library is copied from official api-22. New chart methods are
virtual calls and introduce no new exported free functions. Windows and macOS
compatibility still require their platform builds and load tests.
