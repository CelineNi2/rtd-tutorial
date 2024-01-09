Rooms Class
============

Room Entity
-----------

.. code-block:: java

  @Id
  @GeneratedValue
  private Long id;

  @Column(nullable=false)
  private Integer floor;

  @Column(nullable=false)
  private String name;

  @OneToOne
  private SensorEntity currentTemperature;

  @Column
  private Double targetTemperature;

  @OneToMany(mappedBy = "room", fetch = FetchType.EAGER)
  private Set<WindowEntity> windows = Set.of();

  @OneToMany(mappedBy = "room", fetch = FetchType.EAGER)
  private Set<HeaterEntity> heaters = Set.of();

  @ManyToOne(optional = false)
  private BuildingEntity building;

