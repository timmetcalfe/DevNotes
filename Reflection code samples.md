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

```
var eventTypes = AppDomain.CurrentDomain.GetAssemblies()
                        .SelectMany(assembly => assembly.GetTypes())
                        .Where(type => typeof(IMessageDefinition).IsAssignableFrom(type) && !type.IsInterface);

foreach (var type in eventTypes)
{
    var propertyInfo = type.GetProperty("TopicName");
    if (propertyInfo is not null)
    {
        object typeInstance = typeof(IMessageDefinition);
        var createInstance = Activator.CreateInstance(type);
        if (createInstance is not null)
        {
            typeInstance = createInstance;
        }

        var topicNameValue = propertyInfo.GetValue(typeInstance);
        if (!string.IsNullOrEmpty(topicNameValue?.ToString()))
        {
            topicNames.Add(topicNameValue.ToString()!);
        }
    }
}
```
