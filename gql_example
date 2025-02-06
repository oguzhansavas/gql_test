from gql import gql, Client
from gql.transport.requests import RequestsHTTPTransport

# Define the transport layer with the GraphQL endpoint
transport = RequestsHTTPTransport(
    url="",
    headers={"Authorization": "Bearer "} 
)

# Create a GraphQL client
client = Client(transport=transport, fetch_schema_from_transport=True)

# Define GraphQL query correctly with variables
query = gql("""
    query timeSeries($codes: [String!]!, $startPeriod: String!, $endPeriod: String!) {
        timeSeries(
            codes: $codes
            startPeriod: $startPeriod
            endPeriod: $endPeriod
        ) {
            code
            type
            version
            interval
            nanHandling
            unit
            points {
                time
                value
            }
        }
    }
""")

# Step 4: Define variables properly
params = {
    "codes": ["PRODOC_8710000001214_GSTPTRADE"],
    "startPeriod": "2023-11-11T23:00:00.000Z",
    "endPeriod": "2023-11-12T23:00:00.000Z"
}

# Step 5: Execute the query
response = client.execute(query, variable_values=params)

# Step 6: Process the response
print(response)
