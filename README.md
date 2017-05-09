# Favorite-CSharp-Extension-Classes
These are my favorite C# extension classes I've written.

LineItemsExtensions - The best beast in this set is the ExtractObject<T>() method!  This unassuming method allows the coder to match virtually any Regex patterns they create to a custom class they define!  Requires the Regex pattern to include a tag immediately preceding any group match, indicated in parenthesis () . Each property name in the Regex must EXACTLY correspond to a property name from the custom class (ex: Person).  Once they've constructed a 'Person' class and a string pattern, they can extract 'PersonLines' from plain text so long as each line of plain text sent to my method matches their regex, its groups and class properties.  The method will return a completed instance of your class per line!  Failure to provide adequate patterns (i.e. non matches) or unequal groups/properties will result in warnings, which may be turned off.  Be sure to be using C# 6.0 compiler/VS2015!

    ***EXAMPLE***
    CLASS    
    public class Person { string Name {get;set} string Age {get;set} }
    
    CALL:    
    string input_str = "    Michael Preston         28 2.1 blah junk"; //from a plain text file, xml, json, whatever you can Regex your way out of!
    string regex_pattern = @"\s*(?<Name>[a-zA-Z]+)\s*(?<Age>\d+)";
    Person person_1 = input_str.ExtractObject<Person>(regex_pattern, false);
    person_1.Dump("person object extracted"); //Dump() prints serialized JSON
    
    RESULT:
    person object extracted:
    {
      "Name": "Preston",
      "Age": 28
    }
   

Datatable Extensions - Centered around the ADO.NET datatable, these extensions should aid in manipulating or transforming a given DataTable object.  Favorite example is the 'ToList<T>()' and 'ToDataTable<T>' methods as these come in handy when converting from lists of T to DataTables of T and back again!  Beats writing row["colname"].ToString() repeatedly!  NLog is optional, get it with NuGet!


