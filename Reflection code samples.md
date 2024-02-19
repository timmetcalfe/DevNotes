# Reflection code samples

```
private static IMessageDefinition GetMessageDefinition(string eventTypeName, string eventId)
{
    return (IMessageDefinition)Activator.CreateInstance(FindEventTypeInAssembly("Assessment.IntegrationServices.Core", eventTypeName + "MessageDefinition", eventId))!;
}

private static Type FindEventTypeInAssembly(string assemblyName, string typeName, string eventId)
{
    Assembly assembly = Assembly.Load(assemblyName);
    foreach (Type type in assembly.GetTypes())
    {
        if (type.FullName!.Contains(typeName))
        {
            return type;
        }
    }
    throw new TypeLoadException($"Type '{typeName}' could not be found in assembly '{assemblyName} for EventId {eventId}'.");
}
```
