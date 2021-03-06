import React from 'react'

export default ({url, Page, Endpoint, Resource}) =>
   <Endpoint
      url={url}
      group="network"
      method="post"
      path="/network"
      weight={10}>

      <Endpoint.Return code="201">
         With the newly created <Resource.Link resource="network/:network">network resource</Resource.Link>
      </Endpoint.Return>

      <Endpoint.Return code="401">
         <Resource.Link resource="error/no-auth">error object</Resource.Link> caused by lack off, or failed
         authentication.
      </Endpoint.Return>

      <Endpoint.Return code="403">
         When restricted a <Resource.Link resource="error/auth">error object</Resource.Link> is returned
      </Endpoint.Return>

      <Endpoint.Return code="404">
        If any members of the <code>parents</code> field is non-existing,
        ie the <Resource.Link resource="user">user</Resource.Link> or
        the <Resource.Link resource="organization/:org">organization</Resource.Link> does not exist.
      </Endpoint.Return>

      <Endpoint.Parameter param="network">
        The key of the <Resource.Link resource="network/:network">Network</Resource.Link> resource
      </Endpoint.Parameter>

      <p>
        Creates a new network resource.
      </p>

      <h4>Automatic Parent Assignment</h4>

      <p>
        By default the authenticated entity will be assigned as the sole parent. If desired multiple
        parents can be added AS LONG AS: <em><b>a)</b> the user added exists</em>, <em><b>b)</b> the authenticated entity have
        access to the organization.</em>
      </p>

   </Endpoint>
